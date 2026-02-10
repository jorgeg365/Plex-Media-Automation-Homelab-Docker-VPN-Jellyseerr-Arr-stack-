# Plex-Media-Automation-Homelab-Docker-VPN-Jellyseerr-Arr-stack-
Media Automation Homelab (Plex + Jellyseerr + *Arr + VPN

This repository documents my self-hosted media automation homelab built on a NAS using Docker.  
The goal of this lab is to provide **Netflix-style media requests**, **fully automated downloads**, and **VPN-protected torrenting**, while keeping management services accessible and reliable on the local network.

This project demonstrates real-world Docker networking, VPN isolation, and service orchestration.

---

## 🚀 What This Homelab Does

- Users request movies or TV shows via **Jellyseerr**
- Requests are sent to **Radarr (movies)** or **Sonarr (TV)**
- Indexers are queried via **Jackett**
- Torrents are downloaded using **qBittorrent**
- All torrent traffic is forced through **Gluetun (Surfshark VPN + kill switch)**
- Media is automatically renamed, organized, and added to **Plex**

---

## 🧩 Services Used

| Service | Purpose |
|------|------|
| **Plex** | Media server & streaming |
| **Jellyseerr** | User-friendly request system (Plex login) |
| **Radarr** | Automated movie management |
| **Sonarr** | Automated TV show management |
| **Jackett** | Torrent indexer aggregator |
| **qBittorrent** | Torrent client |
| **Gluetun** | VPN container (Surfshark OpenVPN + firewall) |
| **Docker** | Container orchestration |

---

## 🏗️ Architecture Overview

### Key Design Principle
Only the torrent client is placed behind the VPN.

- **Behind VPN:** qBittorrent  
- **Normal LAN access:** Jellyseerr, Sonarr, Radarr, Jackett, Plex  

This prevents VPN-related breakage while ensuring torrent traffic never leaks.

---

## 🧭 Request & Download Flow

1. User requests content in **Jellyseerr**
2. Jellyseerr sends request to **Radarr** or **Sonarr**
3. Radarr/Sonarr search indexers via **Jackett**
4. qBittorrent downloads content
5. Traffic is routed through **Gluetun (Surfshark VPN)**
6. Media is imported into the library
7. Plex detects and serves the content

---

## 🐳 Docker Deployment Overview

### Folder Structure
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
