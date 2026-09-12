# `pved` k3s-server Decommission Audit

Audit date: 2026-09-11 (America/New_York)

Scope: read-only inspection of Proxmox VM 200 (`k3s-server`) on `pved` before permanent deletion.

## Recommendation

Do not permanently delete the VM yet. It appears safe to shut down for a quarantine period, but it has no current recoverable Proxmox backup and still contains local persistent data.

Recommended sequence:

1. Create and verify a Proxmox backup of VM 200.
2. Shut down the VM without deleting it.
3. Leave it offline for one or two weeks while validating the migrated services.
4. Specifically verify Forgejo, Medspa, Vault/login, Zigbee2MQTT, dashboards, and object storage.
5. Permanently delete the VM only after the validation period succeeds.

## Runtime findings

- The VM was running and configured to start automatically.
- The single-node k3s cluster was healthy from Kubernetes' perspective.
- No application workloads were running. Application deployments were explicitly scaled to zero.
- The only running pods were Kubernetes infrastructure and maintenance components: CoreDNS, Traefik, MetalLB, cert-manager, metrics-server, local-path-provisioner, External Secrets support components, Promtail, and the Velero node agent.
- No established external client connections were observed. Established connections were internal Kubernetes control-plane and pod traffic.
- Docker had no standalone containers or volumes; workloads were managed by k3s/containerd.
- cert-manager was reporting challenge errors because the Cloudflare API token secret was absent.

Application deployments scaled to zero included:

- Forgejo
- Grafana
- Homarr
- Keycloak and its PostgreSQL database
- Loki
- ManimFX
- Medspa variants, PostgreSQL, and MinIO
- MinIO
- Penpot frontend, backend, exporter, Redis, and PostgreSQL
- Supa-test
- Vault and its injector
- Wakeforge
- Zeroclaw
- Zigbee2MQTT, Mosquitto, habit tracker, and PostgreSQL

## Persistent-data findings

The cluster still had 17 bound local-path persistent volumes using approximately 2.4 GB on the VM's disk. The largest or most important volumes included:

| Workload | Approximate data size |
| --- | ---: |
| Forgejo shared storage | 2.0 GB |
| Loki | 84 MB |
| Medspa PostgreSQL | 71 MB |
| Keycloak PostgreSQL | 69 MB |
| Penpot PostgreSQL | 66 MB |
| Grafana | 51 MB |
| Habits PostgreSQL | 47 MB |
| Homarr | 5.8 MB |

Smaller volumes were also present for Vault, MinIO, Mosquitto, Zigbee2MQTT, and several empty application data/cache claims.

Most persistent-volume files were last modified between February 25 and February 27, 2026. The newest observed writes were to Vault and Medspa MinIO data on April 29, 2026. No newer persistent-volume writes were found during the audit.

## Backup findings

- The VM had no Proxmox snapshots.
- `pved` had no configured Proxmox backup jobs.
- No local Proxmox backup archives or recent `vzdump` tasks were found for the VM.
- Velero's backup storage location reported `Unavailable`.
- The most recent completed Velero backups were from February 15, 2026.
- Other recorded Velero backups were partially failed or failed validation.

The existing Velero state should not be treated as sufficient recovery coverage.

## Migration cross-check

- The old cluster still contained a stale Traefik/MetalLB service address, but that address was actually owned by the running Cloudflared LXC on `pve1`, not by the old VM. This supports the conclusion that ingress traffic has moved away from `k3s-server`.
- A dedicated Forgejo LXC was running on `pve2`.
- `k3s-test` was running on `pve1`.
- `k3s-prod` on `pve1` and `k3s-staging` on `pve2` were stopped at audit time. This should be intentional and understood before deletion.

## Conclusion

There was no evidence of a currently serving application on `k3s-server`, and its stored application data appeared dormant for several months. The remaining deletion risk is recoverability, not active traffic: the VM contains the last local copies of several persistent volumes and has no dependable current backup.
