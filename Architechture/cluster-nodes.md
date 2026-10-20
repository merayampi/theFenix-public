---
title: Cluster Hardware Overview
status: active
---

# Cluster Node Architecture

The `theFenix` cluster utilizes distributed, repurposed hardware to maintain a lightweight power footprint while maximizing utility and ensuring high availability for core services.

### Node 01: zapDos
* **Role**: Primary heavy-compute and storage anchor.
* **OS**: Debian/Linux
* **Hardware**: Intel Core i5, 16GB RAM, NVMe OS Drive.
* **Workloads**: PostgreSQL databases, Immich (Media Management), Media Streaming, Container orchestration.
* **Storage Tiering**: Houses the primary storage arrays for active media and cold vaulting.

### Node 02: molTres
* **Role**: Engineering, operations, and development workstation.
* **OS**: Ubuntu/Linux
* **Hardware**: HP ProBook (AMD Ryzen 5 5600U, 32GB RAM, 500GB NVMe).
* **Workloads**: Technical documentation, secure VPN tunneling, and Docker container management.

### Node 03: articUno
* **Role**: Edge services and network routing.
* **OS**: Debian/Linux
* **Hardware**: HP Stream (4GB RAM, 32GB internal storage).
* **Workloads**: Network-level ad-blocking (AdGuard Home) and lightweight DNS management.
