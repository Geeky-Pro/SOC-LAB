# Reset and Recovery

> Status: draft operational procedure.

## Before an exercise
1. Confirm required VMs boot with expected names and addresses.
2. Confirm Splunk health and available storage.
3. Confirm pfSense rules match the exercise scope.
4. Verify the named clean baseline snapshots.
5. Record snapshot IDs and build version.

## After an exercise
1. Stop attack-generation activity.
2. Remove temporary firewall rules and aliases.
3. Export sanitized evidence and learner reports.
4. Revert affected VMs to approved clean snapshots.
5. Verify isolation and telemetry after restore.
6. Remove temporary accounts, files, and services.

## Recovery guide

| Symptom | Initial checks | Recovery direction |
|---|---|---|
| pfSense UI unavailable | VM console, NIC mapping, management IP, rule order | Restore controlled management path; do not open all interfaces |
| No Splunk events | Source service, route, firewall, receiver, time, parsing | Test one source at a time |
| No Suricata alert | Interface, ruleset, traffic path, package compatibility | Re-test with safe documented signature |
| VM cannot reach gateway | VMnet attachment, NIC mapping, IP/mask, DHCP conflict | Correct one segment at a time |
| Disk pressure | Splunk indexes, retention, noisy sources, snapshots | Preserve evidence and apply documented cleanup |
| VM corrupted | Snapshot integrity, free disk, VM manifest | Restore clean snapshot or rebuild verified image |

Snapshots are not backups. Never restore an untrusted snapshot onto a production or bridged network. After rebuild, update versions, checksums, VMnet map, validation date, and deviations. A rebuild is not equivalent to the baseline until validation passes.
