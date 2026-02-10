# VPN Verification

## Check VPN IP (Gluetun)

```bash
docker exec -it gluetun cat /tmp/gluetun/ip

```
# Confirm qBittorrent Uses Same VPN IP

docker exec -it qbittorrent cat /tmp/gluetun/ip

If both IPs match, torrent traffic is protected.

## Kill Switch Test

docker stop gluetun

