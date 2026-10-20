---
title: Storage Topology
status: active
---

# Tiered Storage Architecture

To prevent heavy I/O operations from bottlenecking primary operating systems, `theFenix` utilizes a strict tiered storage topology spanning multiple dedicated drives.

## The Storage Tiers

1. **The Fast Cache (`tortugaEstuary` - SSD)** 
   * **Purpose:** High-speed processing and incoming data.
   * **Workload:** Handles incoming mobile backups, generated thumbnails, and video transcodes. This keeps user interfaces lightning fast without choking the main server drives.

2. **The Brains & Active Access (`barbosaBay` - HDD)** 
   * **Purpose:** Constant read/write access and database hosting.
   * **Workload:** Hosts heavy PostgreSQL databases and houses everyday, active media libraries.

3. **The Vault (`wickedWench` - Massive HDD)**
   * **Purpose:** Cold storage and sensitive master archives.
   * **Workload:** Strict read-only access for scanning applications. No heavy processing or active system data is stored here, preserving the integrity of the master files.

*Note: Additional auxiliary drives (`whitePearl`, `blackPearl`, `greedDrive`) are utilized for offline backups, encrypted LUKS containers, and redundant syncs.*
