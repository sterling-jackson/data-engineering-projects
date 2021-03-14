
### Project 1: Docker + Python CLI
- Build a Docker image that runs a Python application which accepts --filepath and --delimiter arguments. 
- Use `argparse`, `logging`, `csv` and a multi-processing library of your choice such as `concurrent.futures`. Consider experimenting with both thread and process pooling to see which yields better performance.
- Your application should read the file into memory and append `checksum` and `source_file` to each row.
- Avoid using Pandas for this exercise to better showcase your profiency with the language.

##### Your application should:
- Read the input file and iterate through every row.
- Append a MD5 checksum built from all of the input columns to the end of the row as `checksum`.
- Append the filename to the end of the row as `source_file`.
- Use multi-processing to run multiple processes or threads.
- Write the results out to a new delimited file.

##### Instructions:
- Create your Python application.
- Run your Python aplication against a reasonably small file (< 1 GB).
- Once your application works as expected, create your Dockerfile.
- Create a `build.sh` script that runs your `docker build` command.
- Build your Docker image by running `build.sh`.
- Run your Docker image against a reasonably small file (< 1 GB). Your `docker run` command should look something like `docker run image-name:tag python app.py --filepath="" --delimiter=""`. Consider experimenting using larger files to see how your application behaves.
