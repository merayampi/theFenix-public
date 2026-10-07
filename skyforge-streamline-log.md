# SkyForge Rebuild: Phase 1 Audit

## Objective
Transition zapDos from a media-heavy *arr stack to a streamlined, secure family server (SkyForge). 
Target services: Jellyfin, qBittorrent, Calendars, Kanban boards, and Image Backups.

## Constraints
- **Network Freeze:** No modifications to DNS, DHCP, or active internet routing during the audit phase.
- **Hardware:** zapDos (Debian 13) 
- **Storage:** barbosaBay, tortugaEstuary

## Audit Execution
Ran isolated searches for existing configuration files to prepare for a clean slate, bypassing system `/etc` directories to ensure zero network disruption.

**Command Run:**
`sudo find /opt /home/yampi /mnt/barbosaBay /mnt/tortugaEstuary -type f -name "*.conf" > ~/skyforge_conf_audit.txt`

**Next Steps:**
1. Review `skyforge_conf_audit.txt` to identify which configs belong to the *arr stack.
2. Delete deprecated *arr configurations.
3. Prepare Docker directories for the new family-focused stack.
4. Stage the secondary USB ethernet port for future VLAN external access.
# SkyForge Rebuild: Phase 1 Audit

## Objective
Transition zapDos from a media-heavy *arr stack to a streamlined, secure family server (SkyForge). 
Target services: Jellyfin, qBittorrent, Calendars, Kanban boards, and Image Backups.

## Constraints
- **Network Freeze:** No modifications to DNS, DHCP, or active internet routing during the audit phase.
- **Hardware:** zapDos (Debian 13) 
- **Storage:** barbosaBay, tortugaEstuary

## Audit Execution
Ran isolated searches for existing configuration files to prepare for a clean slate, bypassing system `/etc` directories to ensure zero network disruption.

**Command Run:**
`sudo find /opt /home/yampi /mnt/barbosaBay /mnt/tortugaEstuary -type f -name "*.conf" > ~/skyforge_conf_audit.txt`

**Next Steps:**
1. Review `skyforge_conf_audit.txt` to identify which configs belong to the *arr stack.
2. Delete deprecated *arr configurations.
3. Prepare Docker directories for the new family-focused stack.
4. Stage the secondary USB ethernet port for future VLAN external access.
## Phase 2: Quarantine Execution
The secondary audit located the *arr stack configurations (Radarr, Sonarr, Prowlarr) inside the `flyingDutchman` cluster. 

**Actions Taken:**
- Quarantined Radarr, Sonarr, and Prowlarr configuration folders to `~/skyforge_quarantine/` to safely disable them without permanent deletion.
- Preserved `qBittorrent` and `Nextcloud` directories.
- Preparing to prune the `docker-compose.yml` file to remove deprecated services and isolate Jellyfin and qBittorrent.
## Phase 3: Stack Teardown & Rebuild

The `docker-compose.yml` for `flyingDutchman` was audited. It contained the full *arr stack alongside Jellyseerr.

**Actions Taken:**
- Brought down the `flyingDutchman` docker cluster.
- Quarantined the leftover `jellyseerr` configuration folder.
- Rewrote `docker-compose.yml` to exclusively run `qbittorrent`, `jellyfin`, and `vlc`.
- Spun the clean stack back up.

**Current Active Ports:**
- qBittorrent: 4020
- Jellyfin: 4025
- VLC: 4026

**Next Steps:**
- Verify Jellyfin and qBittorrent are active and accessible.
- Address Nextcloud for family Calendars and Kanban boards.
- Map the secondary USB ethernet port for the external VLAN access.
## Phase 4: Verification and Local Access

**Security Check:**
- The current stack (Jellyfin, qBittorrent, VLC) is strictly localized. 
- External access is currently disabled by design to ensure zero wonky security.
- Future external access will be securely routed through the secondary USB ethernet port via VLAN.

**Container Health:**
- Verified containers are running and stable via Docker logs.
- Jellyfin accessible locally at ZapDos-IP:4025
- qBittorrent accessible locally at ZapDos-IP:4020
- ## Phase 4: Orphan Cleanup and Verification

During the stack rebuild, legacy *arr containers and Jellyseerr were orphaned because they were removed from the compose file while still running. 

**Actions Taken:**
- Executed `docker compose down --remove-orphans` to kill and remove the detached containers.
- Successfully released the `flyingdutchman_default` network.
- Spun the clean stack back up.

**Verification:**
- Confirmed only `jellyfin`, `qbittorrent`, and `vlc` are actively running on the host.
