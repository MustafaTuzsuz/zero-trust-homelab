# Zero Trust Network Access — Netbird Implementation

## Overview
Traditional VPN replaced with Netbird ZTNA — providing 
identity-based, device-level access control with no open 
inbound ports and full microsegmentation.

---

## Why Zero Trust Over VPN?

| Traditional VPN | Zero Trust (Netbird) |
|---|---|
| Trust network perimeter | Never trust, always verify |
| Wide network access once connected | Least-privilege per resource |
| Single point of failure | Distributed, peer-to-peer |
| Difficult IoT segmentation | Native microsegmentation |
| Open inbound ports required | No open ports exposed |

---

## Architecture
Device (Peer) ──── Netbird Agent ──── Netbird Management
│
WireGuard tunnel
│
┌─────────┴──────────┐
│                    │
Nextcloud               n8n
(LXC)                  (LXC)
│
IoT Network
(Segmented)

---

## Security Controls Implemented

- **Device authentication** — each peer requires approval
- **Access policies** — per-service, per-device rules
- **IoT microsegmentation** — isolated network zone, 
  no lateral movement possible
- **No open inbound ports** — attack surface eliminated
- **Encrypted tunnels** — WireGuard protocol (state of the art)
- **Peer revocation** — instant access removal when needed

---

## Access Policy Structure

| Resource | Allowed Peers | Policy |
|---|---|---|
| Nextcloud | Trusted devices only | Read/Write |
| n8n | Admin device only | Full access |
| IoT zone | No cross-zone access | Isolated |
| SSH | Admin device only | Key-based |

---

## Key Security Outcomes

- Attack surface reduced to zero open internet-facing ports
- Lateral movement between IoT and production services blocked
- All access logged and auditable
- Remote access maintained without VPN overhead

---

## Lessons Learned

- Zero Trust requires identity management from day one
- Microsegmentation planning before deployment saves time
- WireGuard significantly faster and more secure than OpenVPN
- Peer approval workflow critical for access governance
