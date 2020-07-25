# Data Engineering Projects
A collection of projects to learn data engineering.

### Project 1: Docker + Python CLI
Build a Docker image that runs a Python application which accepts --filepath and --delimiter arguments.
Use `argparse`, `logging`, `csv` and a multi-processing library of your choice such as `concurrent.futures`.
Avoid using Pandas for this exercise.

##### Your application should:
1. Read the input file and iterate through every row.
2. Append a MD5 checksum built from all of the input columns to the end of the row as `checksum`.
3. Append the filename to the end of the row as `source_file`.

##### Step 1:
1. Create your Python application.
2. Run your Python aplication against a reasonably small file (< 1 GB).
2. Once your application works as expected, create your Dockerfile.
2. Create a `build.sh` script that runs your `docker build` command.
2. Build your Docker image by running `build.sh`.
3. Run your Docker image against a reasonably small file (< 1 GB). Your `docker run` command should look something like `docker run image-name:tag python app.py --filepath="" --delimiter=""`.
