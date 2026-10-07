# SkyForge Rebuild: Phase 1 Audit Findings & Quarantine

## Audit Results
The initial `.conf` audit revealed the following active configurations in `theFenix` cluster:
- **Keep:** `qBittorrent` (under `flyingDutchman`)
- **Keep:** System tools (`btop`, `barrier`)
- **Under Review:** `Nextcloud` (Potential host for Calendars and Kanban)
- **Scrap/Quarantine:** `Aria2` (under `procurement`)

Note: The *arr stack (Radarr, Sonarr, Prowlarr, etc.) utilizes `.xml` and SQLite databases, so a secondary audit was required to locate their configuration paths.

## Execution: The Quarantine Protocol
To safely dismantle the wonky *arr stack and procurement pipeline without risking data loss or triggering network/DNS issues, deprecated services are being moved to an isolated directory.

**Commands Run:**
1. `mkdir ~/skyforge_quarantine`
2. `mv /home/yampi/theFenix/procurement ~/skyforge_quarantine/`
3. `sudo find /home/yampi/theFenix /mnt/barbosaBay /mnt/tortugaEstuary -type f -name "config.xml" > ~/skyforge_arr_audit.txt`

## Next Steps
- Review the `skyforge_arr_audit.txt` output to locate remaining *arr configuration directories.
- Move identified *arr directories into `~/skyforge_quarantine/`.
- Begin scaffolding the `docker-compose.yml` for Jellyfin and qBittorrent.
