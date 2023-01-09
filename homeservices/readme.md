# Overview

Just a bunch of my ready-to-deploy containerized homeservices.

| Service            | Purpose                                                                               | Default port(s) |
| ------------------ | ------------------------------------------------------------------------------------- | --------------- |
| Transmission       | Web-based torrent client, just like qbittorrent. I use `flood` theme                  | 9091            |
| Jellyfin           | Media system. One might say it's a selfhosted Netflix                                 | 8096            |
| Nextcloud          | Accessible from anywhere cloud                                                        | 8080            |
| Grafana-prometheus | Server health monitoring                                                              | 3000, 9090      |
| Yacht              | Container health monitoring                                                           | 8000            |
| Heimdall           | Hub for all these services, no need to bookmark them anymore. Configuration required  | 8081            |

> **NOTE:** you can change the first `port` number in your `docker-compose` files to whatever port number you want, just make sure you didn't break something while deploying services. You can also change your time zone in these files.

## Prerequisites

`docker` and `docker-compose` must be installed.

Installation process:

* You can get `docker` [here](https://docs.docker.com/get-docker/) and `docker-compose` [here](https://docker-docs.netlify.app/compose/install/#prerequisites).

## Usage

Clone this repo: 

```
$ cd ~
$ git clone https://github.com/Starmaster99/headintheclouds.git
```

> **TIP:** Check out `homelab-setup` repo if you are new to this DevOps thing!

Go to `homeservices` folder and then deploy services one-by-one:

```
$ cd ~/headintheclouds/homeservices
$ cd jellyfin
$ docker compose up -d
$ cd ..

and so on...
```
