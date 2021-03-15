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
- Your application should read the CSV, append `checksum` to each row, then write each row to a new file.
- Avoid using Pandas for this exercise to better showcase your profiency with the language.
- See `project-1` to get started.

### Project 2: Postgres + Bulk Loading
- Build a Docker image that runs a Python application which downloads, loads, and transforms a large CSV using Postgres.
- Create staging, archive, and production tables within Postgres to load data into.
- Merge staged data using a primary key and create derived dataset by aggregating loaded data using SQL queries.
- Avoid using Pandas for this exercise to better showcase your profiency with the language.
- See `project-2` to get started.

### Project 3: Simple CSV/JSON File Loader
- Create a metadata-driven file loader using Python and Docker than can validate and load any CSV or JSON file. Consider adding support for SFTP and AWS S3 for bonus points.
- The application should accept `--config` and `--source` arguments. The config file can be JSON or YAML and should include properties for file pattern, delimiter, expected columns/keys, and the destination table. Consider adding support for both append and replace behaviors during loading.
- Use `argparse`, `logging`, `csv`, `json`/`yaml` and a multi-processing library of your choice such as `concurrent.futures`. Consider experimenting with both thread and process pooling to see which yields better performance. Also consider experimenting with files that are larger than your available memory.
- Avoid using Pandas for the exercise to better showcase your proficiency with the language.
- Records should be validated against the expected columns/keys and written separately to accepted/rejected files.
- Your accepted file should be bulk loaded using COPY to the target table. Your COPY command will need to be dynamically generated.
- See `project-3` to get started.

### Project 4: Simple Kafka Consumer & Producer
...
