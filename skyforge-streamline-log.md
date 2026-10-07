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
