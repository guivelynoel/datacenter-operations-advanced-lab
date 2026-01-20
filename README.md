# Data Center Operations  Lab (2 VMs / Dual-NIC)

## Overview
This repository documents a medium+ level, two-node lab designed to simulate
real junior data center technician responsibilities: multi-NIC server deployment,
management vs production network separation, secure remote access, shared storage,
health checks, and incident-style troubleshooting.

All work is performed in a lab environment on VirtualBox (macOS host) using the
latest Ubuntu Server release available.

---

## Lab Goals (What This Proves)
- Deploy and manage multiple Linux servers
- Configure dual NICs per server (Mgmt vs Prod separation)
- Implement static IP addressing using Netplan
- Enable secure SSH for admin access (Mgmt-only binding)
- Deploy shared storage (NFS) on the Prod network
- Validate services, monitor health, and document incidents
- Write professional SOPs and troubleshooting runbooks

---

## Topology (Schema)
See: [diagrams/architecture.txt](diagrams/architecture.txt)  
Details: [diagrams/explanation.md](diagrams/explanation.md)

---

## Environment
- Host: macOS + VirtualBox
- Guest OS: Ubuntu Server (latest)
- Nodes:
  - DC-Node-01 (Infrastructure / Storage / Services)
  - DC-Node-02 (Compute / Client / Validation)

### Networks
- Mgmt (Host-only): 192.168.56.0/24
- Prod (Internal network): 10.10.10.0/24

### IP Plan
| Node | Mgmt IP | Prod IP |
|------|---------|---------|
| DC-Node-01 | 192.168.56.10 | 10.10.10.10 |
| DC-Node-02 | 192.168.56.11 | 10.10.10.11 |

---

## Services Implemented
- SSH remote administration (Mgmt only)
- NFS shared storage (Prod only)
- Baseline health checks and service validation
- Incident simulations + recovery documentation

---

## Evidence & Documentation
- Inventory: [docs/inventory.md](docs/inventory.md)
- Network design: [docs/network-design.md](docs/network-design.md)
- Storage design: [docs/storage-design.md](docs/storage-design.md)
- Security controls: [docs/security.md](docs/security.md)
- SOPs: [docs/procedures.md](docs/procedures.md)
- Troubleshooting runbook: [docs/troubleshooting.md](docs/troubleshooting.md)
- Build notes: [logs/build-notes.md](logs/build-notes.md)
- Incidents: [logs/incidents.md](logs/incidents.md)

---

## Config Examples (Sanitized)
These are documentation examples only (no secrets):
- Netplan examples: [configs/network/](configs/network/)
- NFS exports: [configs/services/nfs-exports.example](configs/services/nfs-exports.example)
- SSH config example: [configs/services/sshd_config.example](configs/services/sshd_config.example)

---

## Author
Guively Noel  
Location: Georgia, USA  
GitHub: guivelyoel  
LinkedIn: 
