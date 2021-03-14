### Project 2: Postgres + Bulk Loading
- Build a Docker image that runs a Python application which downloads, loads, and transforms a large CSV using Postgres.
- Avoid using Pandas for this exercise to better showcase your profiency with the language.

##### Your application should:
- Download the source file from Kaggle.
- Create your objects in Postgres if they don't exist.
- Mount the directory containing the source file to your Docker image.
- Use the COPY command to load into your staging table.
- Merge into your production table, replacing any matches on the primary key.
- Truncate and reload your derived/aggregated table.

##### Instructions:
- Download the [Seattle Library Collection Inventory CSV](https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory) from Kaggle.
  - You can use `head <filename>` to inspect the file to determine which columns to create for the next step.
- Write SQL to create four tables in Postgres: `inventory_staging`, `inventory_archive`, `inventory_production`, and `inventory_derived`. Each table should include a checksum, unique row number, and date created column. Consider also creating an `inventory` view from `inventory_production` for ease of use. You can use `bibnum` as the primary key.
- Implement a method for initializing your data warehouse by running your DDL. This should run the DDL that you prepared previously, creating or recreating all of your tables.
- Implement a method for bulk loading your data files to the `inventory_staging` table. It should remove all previous records from the table before loading the current batch. Use the COPY command to do this.
- Next, create a SQL script that inserts any new records from the batch into `inventory_archive`. You can use checksum to determine this. Finally, create a SQL script that inserts from `inventory_staging` to `inventory_production`, replacing any matches on the primary key.
- Finally, create a SQL script to aggregate data from the inventory table and write it to inventory_derived. This should be a full replacement of what's in inventory_derived. This table should contain individual subject values parsed from the subjects column and grouped by publisher so your final derived table should contain publisher, subject, count, row number and date created.
- Create or pull a Postgres Docker image and launch it so that your application can connect to it.
- Create a Shell script (run.sh) that executes the following steps:
  - Fetch data from Kaggle.
  - Extract and process data to produce outputs.
  - Create data warehouse objects.
  - Bulk load outputs to inventory table.
  - Truncate and recreate derived table.
- Run your Docker image to see what happens. You will need to mount the directory containing your source file to the Docker image using `-v`. Your `docker run` command should look something like `docker run -v <project-directory>:<container-directory> image-name:tag bash run.sh`.
- After it works correctly, add your solution to Github and try the next project (or try this one again using a different language!)

##### Troubleshooting
- If your system has memory problems, you could break the CSV into smaller chunks and then process the chunks one at a time.
  - You can use `split -l <chunk-size> <source-file> <output-file>` command to do this.
- Launch an interactive connection to your Docker image by including `-it` in your `docker run` command. It should looking something like `docker run -it -v <project-directory>:<container-directory> image-name:tag bash`.
  - You can use this if your system doesn't support commands like `head` and `split`.