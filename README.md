# doco

A simple script for managing multi layer docker compose files

## Installation

```
# Package not yet on the AUR!
yay -S doco
```

## Motivation

I had a huge docker-compose file for all my services and wanted to split them into smaler chunks.
That made it harder to use with docker compose so I came up with this script.

My structure looks like this:

```
.
├── filesharing
│   ├── compose.filesharing.yaml
│   ├── syncthing
│   └── webdav
├── internal-services
│   ├── compose.internal.yaml
│   └── homer
├── network
│   ├── blocky
│   ├── compose.network.yaml
│   ├── diun
│   ├── omada
│   └── wg-easy
├── public-services
│   ├── compose.public.yaml
│   ├── photoview
│   ├── remark42
│   ├── shiori
│   ├── vaultwarden
│   └── vikunja
├── smarthome
│   ├── compose.smarthome.yaml
│   ├── homeassistant
│   ├── influxdb
│   ├── mosquitto
│   └── postgresql
└── webserver
    ├── caddy
    ├── compose.webserver.yaml
    └── www
```

The script searches for all `compose.*.yaml` files and joins them with `docker compose -f` and runs the commands with that.

## Usage

```
doco update # docker compose pull --ignore-pull-failures && docker compose up -d

doco status # docker compose ps -a

doco lf # docker compose logs -f

doco clean # docker system prune --volumes

doco <command> # passes command to docker compose, for exampe doco restart caddy gets docker compose restart caddy

```
