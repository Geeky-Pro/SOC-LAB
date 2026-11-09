# Virtual Machine Resource Planning

> Status: initial planning ranges, not guaranteed simultaneous-run sizing or vendor minimums.

| VM | vCPU | RAM | Disk | Notes |
|---|---:|---:|---:|---|
| pfSense + Suricata | 2 | 2–4 GB | 20–30 GB | Increase for inspection load |
| Splunk Enterprise | 4 | 8–16 GB | 80–150 GB | Dominant memory/storage consumer |
| Windows | 2–4 | 4–8 GB | 60–80 GB | Sysmon volume affects ingest |
| Ubuntu web | 2 | 2–4 GB | 25–40 GB | Minimal service |
| Kali | 2 | 4 GB | 40–60 GB | Increase for specific workloads |
| Mailpit optional | 1–2 | 1–2 GB | 10–20 GB | Small local service |

## Sizing procedure
1. Inventory host RAM, CPU threads, free disk, and virtualization support.
2. Determine which VMs must run simultaneously for each practical.
3. Reserve capacity for the host OS and VMware.
4. Estimate Splunk daily ingest and retention; tune noisy Sysmon and IDS sources.
5. Reassess after a complete lab run and record observed peak use.

If a host cannot run all VMs concurrently, define and test a staged schedule. Do not claim an integrated scenario was completed when a required source was offline.

Snapshots are rollback points, not backups. Keep VM images outside Git and maintain a version/checksum manifest.
