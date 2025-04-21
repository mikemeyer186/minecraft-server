# Minecraft Server

This repository contains the configuration of a Minecraft Java Server in a docker container. You can run it on your local machine or on your server. The Minecraft Server is configured to run with the latest version of Minecraft and has some basic settings for configuration. As a container image the popular image of `itzg/minecraft-server` is used, which is supported by the Minecraft community.

You can find further information on the following websites:<br>
https://github.com/itzg/docker-minecraft-server<br>
https://minecraft.wiki/w/Tutorial:Setting_up_a_Java_Edition_server

<br>

## Prerequisites

-   Server with Docker and Docker Compose installed
-   Alternatively, you can run it on your local machine
-   Git installed to clone the repository
-   Python3 (optional, if you want to run mcstatus)

<br>

## Getting started

1. Clone the repository:

```shell
git clone git@github.com:mikemeyer186/minecraft-server.git
```

2. Change to directory `/minecraft-server`:

```shell
cd minecraft-server
```

3. Run the Docker Compose file:

```shell
docker compose up -d
```

4. Connect to the server:

-   Open Minecraft Java Client and click on "Multiplayer"
-   Add the server address: `<ip-address>:8888`
-   Enjoy playing Minecraft!

5. Stop the server:

```shell
# Stop the server, but keep the data saved
docker compose down

# or stop the server and remove all data
docker compose down -v
```

<br>

## mcstatus (optional)

This repository also contains the `mcstatus` package, which is a Python script that can be used to check the status of a Minecraft server. It can be used to check if the server is online or offline, and it can also be used to get the number of players online.

1. Create and activate virtual environment:

```shell
python -m venv <name of your environment>
source <name of your environment>/bin/activate
```

2. Install dependencies:

```shell
pip install -r requirements.txt
```

3. Run the script:

```shell
mcstatus <ip-address>:<port> status
```

<br>

## Configuration

The server can be configured with some basic settings. These settings can easily changed within the `docker compose` command. These settings are optional and can be left out. The default values will be used in this case. All other official settings of a Minecraft Server are default values.

| Settings       | Available values                                                      | Default          |
| -------------- | --------------------------------------------------------------------- | ---------------- |
| SERVER_NAME    | Your server name                                                      | `Peaceful World` |
| LEVEL_TYPE     | `normal`, `flat`, `large_biomes`, `amplified`, `single_biome_surface` | `flat`           |
| MAX_PLAYERS    | Integer from 0 - (2^31 - 1)                                           | `5`              |
| MAX_WORLD_SIZE | Integer from 1 - 29999984                                             | `1000`           |
| DIFFICULTY     | `peaceful`, `easy`, `normal`, `hard`                                  | `peaceful`       |

### Example

Configure the server with the following command:

```shell
LEVEL_TYPE=normal MAX_PLAYERS=20 MAX_WORLD_SIZE=1000 DIFFICULTY=easy docker compose up -d
```
