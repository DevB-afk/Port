# DevFlix (Jellyfin)

## Overview

DevFlix is a Jellyfin server running as a container on the Proxmox host. It doesn't store any media itself. The library lives on the OpenMediaVault NAS and is mounted into the container over the network.

```
Disc ──► HP ProDesk (rip) ──► OMV NAS (share) ──► Proxmox container (Jellyfin) ──► clients
```

## Media workflow

1. Rip the Blu-ray or DVD on the HP ProDesk.
2. Copy the file to the NAS media share, named the way Jellyfin expects:
   ```
   Movies/
   └── Movie Title (Year)/
       └── Movie Title (Year).mkv
   Shows/
   └── Show Name/
       └── Season 01/
           └── Show Name S01E01.mkv
   ```
3. Jellyfin picks it up on the next library scan.

## Remote access

Clients connect through Tailscale, so the server is never exposed to the public internet.

## Notes and to-dos

- [ ] Pass the Inspiron's GPU through for hardware transcoding
- [ ] Document the exact share mount settings used in the container
