
---

# 📄 `docs/configuration.md`

```md
# Configuration

## Jellyseerr

- Connected using Plex OAuth
- Radarr added as default movie server
- Sonarr added as default TV server
- Root folders and quality profiles selected

## Sonarr

- qBittorrent configured as download client
- Indexers added via Jackett
- Root folder: /tv

## Radarr

- qBittorrent configured as download client
- Indexers added via Jackett
- Root folder: /movies

## Jackett

- Only stable public indexers used
- Cloudflare-heavy indexers avoided where possible

Important Startup Order

qBittorrent must start after Gluetun:

docker restart gluetun
sleep 15
docker restart qbittorrent

