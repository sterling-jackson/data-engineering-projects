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
- Write SQL to create two tables in Postgres: `inventory` and `inventory_derived`. Both tables should include a checksum, unique row number, and date created column.
- Implement a method for initializing your data warehouse by running your DDL. This should run the DDL that you prepared previously.
- Implement a method for bulk loading your data files to the inventory table, replacing any existing records on primary key with the matching input record.
- Create a SQL script to aggregate data from the inventory table and write it to inventory_derived. This should be a full replacement of what's in inventory_derived. This table should contain individual subject values parsed from the subjects column and grouped by publisher so your final derived table should contain publisher, subject, count, row number and date created.
- Create or pull a Postgres Docker image and launch it.
- Download 
- Your docker run command should mount your application directory to the Docker container.
- Create a Bash script (run.sh) that executes the following steps:
  - Fetch data from Kaggle.
  - Extract and process data to produce outputs.
  - Create data warehouse objects.
  - Bulk load outputs to inventory table.
  - Truncate and recreate derived table.
- See `project-2` to get started.
