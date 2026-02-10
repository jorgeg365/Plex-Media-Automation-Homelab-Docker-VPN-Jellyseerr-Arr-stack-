Expected:

qBittorrent loses internet access immediately


---

# 📄 `docs/troubleshooting.md`

```md
# Troubleshooting

## qBittorrent Web UI Not Loading After Reboot

Cause:
qBittorrent started before Gluetun was ready.

Fix:
```bash
docker restart gluetun
sleep 15
docker restart qbittorrent
