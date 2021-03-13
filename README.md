# Data Engineering Projects
A collection of projects to learn data engineering and demonstrate proficiency with the various tools, technologies, and concepts that are relevant within the data engineering field.

### Recommendations

- [Google's Style Guide for Python](https://google.github.io/styleguide/pyguide.html) is an excellent resource for style recommendations.
- Choose and use a consistent style when writing SQL.
- You should generally try to include functions/methods, logging, exception handling, type anotations, helpful comments, and intuitive naming conventions.
- Including unit tests is always a good idea.

### Project 1: Docker + Python CLI
- Build a Docker image that runs a Python application which accepts --filepath and --delimiter arguments.
- Use `argparse`, `logging`, `csv` and a multi-processing library of your choice such as `concurrent.futures`. Consider experimenting with both thread and process pooling to see which yields better performance.
- Avoid using Pandas for this exercise to better showcase your profiency with the language.
- See `project-1` to get started.

### Project 2: Postgres + Bulk Loading
- Download the [Seattle Library Collection Inventory CSV](https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory) from Kaggle. Consider automating the download process for bonus points.
- Write SQL to create four tables in Postgres: `inventory_staging`, `inventory_archive`, `inventory_production`, and `inventory_derived`. Each table should include a checksum, unique row number, and date created column. Consider also creating an `inventory` view from `inventory_production` for ease of use.
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

### Project 3: CSV/JSON File Loader
- Create a metadata-driven file loader using Python and Docker than can validate and load any CSV or JSON file. Consider adding support for SFTP and AWS S3 for bonus points.
- The application should accept `--config` and `--source` arguments. The config file can be JSON or YAML and should include properties for file pattern, delimiter, expected columns/keys, and the destination table. Consider adding support for both append and replace behaviors during loading.
- Use `argparse`, `logging`, `csv`, `json`/`yaml` and a multi-processing library of your choice such as `concurrent.futures`. Consider experimenting with both thread and process pooling to see which yields better performance. Also consider experimenting with files that are larger than your available memory.
- Avoid using Pandas for the exercise to better showcase your proficiency with the language.
- Records should be validated against the expected columns/keys and written separately to accepted/rejected files.
- Your accepted file should be bulk loaded using COPY to the target table. Your COPY command will need to be dynamically generated.
- See `project-3` to get started.
