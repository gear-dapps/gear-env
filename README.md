# Gear Envinronment

Development environment for building smart contracts.

# Usage

0. Install [Docker](https://docs.docker.com/engine/install/).

1. Pull and run Docker container:

    ```shell
    docker pull ghcr.io/gear-dapps/gear-env:latest
    ```

    Linux:

    ```shell
    docker run --rm --name gear-env -itd gear-env bash
    ```

    macOS:

    ```shell
    docker run --rm --name gear-env --platform linux/amd64 -itd gear-env bash
    ```

2. Prepare smart contract for building (here we use [`app`](https://github.com/gear-dapps/app) for example):

    ```shell
    git clone https://github.com/gear-dapps/app.git --depth 1
    docker cp ./app gear-env:/root
    ```

3. Build smart contract on the Docker container:

    ```shell
    docker exec -itw /root/app gear-env cargo build --release
    ```

-. Stop the Docker container after using:

    ```shell
    docker stop gear-env
    ```

# Contents

- Based on Ubuntu 22.04 LTS
- Rust toolchain: `v1.69` (`stable`) and `1.71.0-nightly` (`2023-04-13`)
- Node.js: `v18.16`
- Yarn: `v1.22`
- Gear node binary: `v0.1.4-5c685d0`

# Build Docker image locally

## On macOS

```shell
docker build --platform linux/amd64 --ulimit nofile=1024000:1024000 -t gear-env docker
```

## On Linux

```shell
docker build --ulimit nofile=1024000:1024000 -t gear-env docker
```

# License

The source code is licensed under the [MIT license](LICENSE).
