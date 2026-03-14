# Architecture

## Design Principle

Only qBittorrent is placed behind the VPN.
Everything else runs on the normal Docker/LAN network.

This avoids:
- Broken Web UIs
- Slow API calls
- VPN-caused instability

---

## Network-Level Diagram

```mermaid
flowchart TB
  User[User / Phone / Browser]

  subgraph LAN["Home LAN"]
    Plex[Plex]
    Jellyseerr[Jellyseerr]
    Sonarr[Sonarr]
    Radarr[Radarr]
    Jackett[Jackett]
  end

  subgraph VPN["VPN Namespace"]
    Gluetun[Gluetun<br/>Surfshark VPN]
    qBit[qBittorrent]
  end

  Internet[(Internet)]

  User --> Jellyseerr
  Jellyseerr --> Sonarr
  Jellyseerr --> Radarr
  Sonarr --> Jackett
  Radarr --> Jackett
  Sonarr --> qBit
  Radarr --> qBit
  qBit --> Gluetun --> Internet
  Plex --> User
