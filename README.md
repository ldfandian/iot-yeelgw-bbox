# iot-yeelgw-bbox

This is a build box environment for the yl gateway project.

## Dependency

* [Docker](https://www.docker.com/) - Use containers to Build, Share and Run your applications


## Usage

* You can sync the repo and build your own Docker iamge locally.

* Also, you can directly use the [pre-built docker hub repository](https://hub.docker.com/repository/docker/ldfandian/iot-yeelgw-bbox) on hub.docker.com .

  * Pull the docker iamge
  ```
  docker pull ldfandian/iot-yeelgw-bbox:latest
  ```

  * Start the centos 7.9 build box
  ```
  docker run -it -v <your_local_sourcecode_directory>:/mnt/devroot/ -v ~/.ssh:/root/.ssh --cpus=6 --memory 16GB --pids-limit=-1 -w /mnt/devroot/ --name iot-yeelgw-bbox-container ldfandian/iot-yeelgw-bbox:latest /bin/bash
  ```

