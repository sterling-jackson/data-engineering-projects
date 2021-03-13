# Data Engineering Projects
A collection of projects to learn data engineering and demonstrate proficiency with the various tools, technologies, and concepts that are relevant within the data engineering field.

### Recommendations

- [Google's Style Guide for Python](https://google.github.io/styleguide/pyguide.html) is an excellent resource for style recommendations.

### Project 1: Docker + Python CLI
- Build a Docker image that runs a Python application which accepts --filepath and --delimiter arguments.
- Use `argparse`, `logging`, `csv` and a multi-processing library of your choice such as `concurrent.futures`.
- Include functions/methods, logging, exception handling, type anotations, helpful comments, and intuitive naming conventions. 
- Avoid using Pandas for this exercise.
- See `project-1` to get started.

### Project 2: Postgres + COPY
- Download the [Seattle Library Collection Inventory CSV](https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory) from Kaggle. Bonus points if you automate the download.
- Write SQL to create four tables in Postgres: `inventory_staging`, `inventory_archive`, `inventory_production`, and `inventory_derived`. Both tables should include a checksum, unique row number, and date created column. Consider also creating an `inventory` view from `inventory_production` for ease of use.
- Implement a method for initializing your data warehouse by running your DDL. This should run the DDL that you prepared previously, creating or recreating all of your tables.
- Implement a method for bulk loading your data files to the `inventory_staging` table. It should remove all previous records from the table before loading the current batch. Use the COPY command to do this.
- Next, create a SQL script that inserts any new records from the batch into `inventory_archive`. You can use checksum to determine this. Finally, create a SQL script that inserts from inventory_staging to inventory_production, replacing replacing any existing records on primary key.
- Finally, create a SQL script to aggregate data from the inventory table and write it to inventory_derived. This should be a full replacement of what's in inventory_derived. This table should contain individual subject values parsed from the subjects column and grouped by publisher so your final derived table should contain publisher, subject, count, row number and date created.
- Create or pull a Postgres Docker image and launch it so that your application can connect to it.
- Create a Bash script (run.sh) that executes the following steps:
  - Fetch data from Kaggle.
  - Extract and process data to produce outputs.
  - Create data warehouse objects.
  - Bulk load outputs to inventory table.
  - Truncate and recreate derived table.
- See `project-2` to get started.
