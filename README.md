# Mediabox in a docker-compose

Fancy a convenient way to load up your containers?

Written for personal use only.

## Prerequisites
1. Docker `curl -sSL https://get.docker.com/ | sh`
2. [docker-compose](https://docs.docker.com/compose/install/) `sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose && docker-compose --version`

## Deploy
1. Download `docker-compose.yaml`
2. Run `docker-compose up -d`
3. ???
4. Profit!

## Links to Docker images
- [Organizr](https://hub.docker.com/r/lsiocommunity/organizr/)
- [Transmission](https://hub.docker.com/r/linuxserver/transmission/)
- [Suitarr (Jackett + Sonarr + Radarr + Lidarr)](https://hub.docker.com/r/hotio/suitarr/)
- [Transmission-RSS](https://hub.docker.com/r/reverie89/transmission-rss/)

## Note
- `127.0.0.1` is added in front of `ports` parameters. This is to force Docker to expose container's port (with the `127.0.0.1`) only to the local host machine. Although [YMMV](https://dictionary.cambridge.org/dictionary/english/ymmv), my `iptables` rules are overridden (at least for me) to open the ports to the outside world - this can be a potentially dangerous unintended consequence especially without being a firewall! I have a webserver running on the local host machine (also why I forwarded organizr to use port 9000 instead), so I set up reverse proxies for the services. You might want to consider doing the same.
- You may want to change `TZ=<timezone>` parameter under `transmission`'s `environment` to where you actually are. Here's a [reference](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
