# Doxygen in Docker
Running Doxygen in Docker.

## Description
You should run the container by mounting the current to `/mnt/workspace`. The Docker container `cd` into that directory and run `doxygen`, so relative paths should be used in the `Dockerfile`. UID and GID are passed to the Docker to ensure files that are created would be own by the runner.


## Building
```bash
docker build -t <tag> .
```

## Usage
- For one time usage, you can run the following command after building, append any argument at the end to pass to Doxygen:

  ```bash
  docker run -it --rm -v $(pwd):/mnt/workspace <tag> $(id -u) $(id -u)
  ```

- Alternatively, you can make a function in the `.bashrc` as below and call `doxygen` as usual binary:

  ```bash
  doxygen () {
    docker run -it --rm -v $(pwd):/mnt/workspace <tag> $(id -u) $(id -u) $@
  }
  ```
