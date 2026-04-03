# Nextcloud — Self-Hosted Deployment

## Overview
Nextcloud deployed as LXC container on Proxmox VE, providing 
self-hosted file storage, sync, and collaboration — fully under 
personal control with no third-party data exposure.

---

## Deployment Specs

| Component | Details |
|---|---|
| Deployment type | LXC Container (Proxmox) |
| Access | HTTPS only |
| Authentication | Strong password + 2FA enabled |
| Storage | Local disk with snapshot backup |
| Availability | 99%+ uptime |
| Network access | Via Netbird ZTNA only — no open ports |

---

## Security Configuration

- **HTTPS enforced** — self-signed certificate, no plain HTTP
- **2FA enabled** — TOTP-based second factor
- **Access restricted** — Netbird Zero Trust layer required
- **No public internet exposure** — zero open inbound ports
- **Automatic updates** — security patches applied promptly
- **Snapshot backup** — daily automated recovery points

---

## Integration with Homelab Stack

User Device
│
▼
Netbird ZTNA (authenticated tunnel)
│
▼
Nextcloud LXC (Proxmox)
│
▼
Local Storage + Snapshot Backup

---

## Operational Notes

- Container resource usage monitored via Proxmox dashboard
- Logs reviewed regularly for failed login attempts
- Storage utilisation tracked — alerts configured at 80% threshold
- Tested full restore from snapshot — recovery time under 5 minutes

---

## Lessons Learned

- LXC containers ideal for Nextcloud — low overhead, fast snapshots
- ZTNA access eliminates need for port forwarding entirely
- 2FA essential even in Zero Trust environment — defence in depth
- Regular snapshot testing critical — untested backups are not backups
- 
