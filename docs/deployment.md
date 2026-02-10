
---

# 📄 `docs/deployment.md`

```md
# Deployment

## Folder Layout

```text
/volume1/docker/
├─ jellyseerr/
│  └─ config/
├─ vpn-stack/
│  ├─ gluetun/
│  └─ qbittorrent/
└─ Media/
   ├─ Downloads/
   ├─ Movies/
   └─ TV Shows/

cd /volume1/docker/vpn-stack
docker compose up -d

cd /volume1/docker/jellyseerr
docker compose up -d
