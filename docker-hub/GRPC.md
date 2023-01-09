<div align="center">

![Skyra Logo](https://cdn.skyra.pw/gh-assets/skyra_avatar.png)

# Skyra Project Grpc

**GRPC Microservice to interact with Skyra Database**

[![Discord](https://discord.com/api/guilds/254360814063058944/embed.png?style=banner2)](https://join.skyra.pw)

</div>

---

**Table of Contents**

-   [Skyra Project Grpc](#skyra-project-grpc)
    -   [Quick reference](#quick-reference)
    -   [How to use this image](#how-to-use-this-image)
        -   [Setting up a Docker Compose file](#setting-up-a-docker-compose-file)
    -   [Using custom configuration](#using-custom-configuration)
        -   [`POSTGRES_PASSWORD`](#postgres_password)
        -   [`POSTGRES_USER`](#postgres_user)
        -   [`POSTGRES_DB`](#postgres_db)
        -   [`POSTGRES_HOST`](#postgres_host)
        -   [`POSTGRES_PORT`](#postgres_port)
    -   [Buy us some doughnuts](#buy-us-some-doughnuts)
    -   [Contributors ✨](#contributors-%E2%9C%A8)

---

## Quick reference

-   **Maintained by**:  
    [Skyra Project](https://github.com/skyra-project)

-   **Where to get help**:  
    [the Skyra Lounge Discord server](https://join.skyra.pw/)

-   **Where to file issues**:  
    [https://github.com/skyra-project/skyra/issues](https://github.com/skyra-project/skyra/issues)

-   **Source of this description**:  
    [Skyra repo `assets/docker-hub` directory](https://github.com/skyra-project/skyra/blob/main/assets/docker-hub/GRPC.md) ([history](https://github.com/skyra-project/skyra/commits/main/assets/docker-hub/GRPC.md))

## How to use this image

### Setting up a Docker Compose file

```yaml
version: '2.4'
services:
    grpc:
        image: skyrabot/grpc:latest
        container_name: 'skyra-grpc'
        depends_on:
            - postgres
        environment:
            - POSTGRES_HOST=postgres
        ports:
            - '8291:80'
    postgres:
        container_name: postgres
        image: skyrabot/postgres:latest
        restart: always
        ports:
            - '5432:5432'
        volumes:
            - postgres-data:/var/lib/postgresql/data
```

[![Try in PWD](https://raw.githubusercontent.com/play-with-docker/stacks/master/assets/images/button.png)](http://play-with-docker.com/?stack=https://raw.githubusercontent.com/skyra-project/skyra/main/assets/docker-hub/playwithdocker-grpc-stack.yml)

## Using custom configuration

Both the GRPC and PostgreSQL images use several environment variables that you can configure.

### `POSTGRES_PASSWORD`

This optional environment variable is used for the `$POSTGRES_USER` to connect to the database. If it is not specified, then the default password of `postgres` will be used.

### `POSTGRES_USER`

This optional environment variable is used in conjunction with `POSTGRES_PASSWORD` to set a user and its password. This variable will create the specified user with superuser power and a database with the same name. If it is not specified, then the default user of `postgres` will be used.

### `POSTGRES_DB`

This optional environment variable can be used to define a different name for the default database that is created when the image is first started. If it is not specified, then the value of `skyra` will be used.

### `POSTGRES_HOST`

This optional environment variable is _only_ for the `skyrabot/grpc` image and can be used to define a different host for the where the database runs relative to the GRPC serivce. If it is not specified, then the value of `localhost` will be used.

### `POSTGRES_PORT`

This optional environment variable is _only_ for the `skyrabot/grpc` image and can be used to define a different port for the where the database runs relative to the GRPC serivce. If it is not specified, then the value of `5432` will be used.

## Buy us some doughnuts

Skyra Project is open source and always will be, even if we don't get donations. That said, we know there are amazing people who
may still want to donate just to show their appreciation. Thanks you very much in advance!

We accept donations through Patreon, BitCoin, Ethereum, and Litecoin. You can use the buttons below to donate through your method of choice.

| Donate With |         QR         |                        Address                         |
| :---------: | :----------------: | :----------------------------------------------------: |
|   Patreon   | ![PatreonImage][]  |                 [Click Here][patreon]                  |
|   PayPal    |  ![PayPalImage][]  |                  [Click Here][paypal]                  |
|   BitCoin   | ![BitcoinImage][]  |     [3JNzCHMTFtxYFWBnVtDM9Tt34zFbKvdwco][bitcoin]      |
|  Ethereum   | ![EthereumImage][] | [0xcB5EDB76Bc9E389514F905D9680589004C00190c][ethereum] |
|  Litecoin   | ![LitecoinImage][] |     [MNVT1keYGMfGp7vWmcYjCS8ntU8LNvjnqM][litecoin]     |

## Contributors

Please make sure to read the [Contributing Guide][contributing] before making a pull request.

Thank you to all the people who already contributed to Sapphire!

<a href="https://github.com/skyra-project/skyra/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=skyra-project/skyra" />
</a>

[contributing]: https://github.com/skyra-project/.github/blob/main/.github/CONTRIBUTING.md[bitcoin]: bitcoin:3JNzCHMTFtxYFWBnVtDM9Tt34zFbKvdwco?amount=0.01&label=Skyra%20Discord%20Bot
[bitcoinimage]: https://cdn.skyra.pw/gh-assets/bitcoin.png
[ethereum]: ethereum:0xcB5EDB76Bc9E389514F905D9680589004C00190c?amount=0.01&label=Skyra%20Discord%20Bot
[ethereumimage]: https://cdn.skyra.pw/gh-assets/ethereum.png
[litecoin]: litecoin:MNVT1keYGMfGp7vWmcYjCS8ntU8LNvjnqM?amount=0.01&label=Skyra%20Discord%20Bot
[litecoinimage]: https://cdn.skyra.pw/gh-assets/litecoin.png
[patreon]: https://donate.skyra.pw/patreon
[patreonimage]: https://cdn.skyra.pw/gh-assets/patreon.png
[paypal]: https://donate.skyra.pw/paypal
[paypalimage]: https://cdn.skyra.pw/gh-assets/paypal.png
