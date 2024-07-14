# QBITTORRENT X HOTSPOTSHIELD

## Setup

1. Go to Hotspot Shield VPN [dashboard](https://app.hotspotshield.com/app/hotspotshield)
2. Go to the "Router" menu
3. Select a virtual location and click on downlaod (you should get an ovpn file)
4. Copy the username / password
5. Open the `.env` and change the env variables. (`QBITTORRENT_CONFIG` should be a path to an empty folder, it'll be where qbittorrent will store its config data)
6. In the ovpn file you need to replace the server hostname by one of its IP addresses (server hostname should be next to the `remote` instruction). If it is not an IP address, you need to DNS resolve it, for example with `nslookup domain.com` and replace the hostname field with one of its corresponding IP addresses.


## Usage

```sh
docker-compose up -d

# Check IP
docker-compose exec qbittorrent-nox wget -qO - https://ipinfo.io/
```

Go to http://localhost:8080

The default username is "admin". To get the password you have to run the `docker-compose logs` command, the initial password should be logged.

## Issues

- If qbittorrent don't have access to internet you can try to uncomment the `FIREWALL=off` line in the `docker-compose.yml`. Definitely not recommended but it should help.
- Ping command in the containers might not work, this is expected.