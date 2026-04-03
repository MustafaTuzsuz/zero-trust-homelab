# Proxmox VE — Setup & Configuration

## Overview
Proxmox VE is the hypervisor backbone of this homelab. 
It manages all virtual machines and LXC containers running 
production workloads 24/7.

---

## Host Specifications

| Component | Details |
|---|---|
| Hypervisor | Proxmox VE 8.x |
| Virtualisation | KVM (VMs) + LXC (containers) |
| Storage | Local + ZFS snapshot support |
| Network | Bridge (vmbr0) + VLAN segmentation |
| Access | Web UI (HTTPS) + SSH (key-based only) |

---

## Running Services

| Service | Type | Purpose |
|---|---|---|
| Nextcloud | LXC Container | Self-hosted file storage & sync |
| n8n | LXC Container | Workflow automation |
| Netbird | LXC Container | Zero Trust Network Access |

---

## Security Hardening Applied

- SSH root login disabled — key-based authentication only
- Proxmox web UI restricted to local network
- Firewall rules configured at host and VM/container level
- Regular snapshots scheduled for all containers
- No unnecessary ports exposed to internet

---

## Snapshot Strategy

- Daily automatic snapshots on all LXC containers
- Retention: 7 days rolling
- Tested restore procedure — verified recovery time < 5 minutes

---

## Network Configuration

- Bridge interface: `vmbr0`
- VLAN segmentation for IoT isolation
- DNS & DHCP managed internally
- All traffic routed through Netbird Zero Trust layer

---

## Monitoring

- Proxmox built-in resource monitoring (CPU, RAM, disk)
- Alert thresholds configured for resource spikes
- Uptime maintained at 99%+

---

## Lessons Learned

- LXC containers significantly more efficient than full VMs 
  for lightweight services
- Snapshot scheduling critical for production stability
- VLAN segmentation essential for IoT device isolation
