# Data Center Operations  Lab (2 VMs / Dual-NIC)

## Overview
this repository documents a hands-on data center operations lab designed to simulate
real-world infrastructure tasks performed by Data Center Technicians, IT Support,
and Junior System Administrators.

The lab focuses on **network segmentation, secure access, shared storage, persistence,
firewall enforcement, incident handling, and operational documentation**.

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
## Architecture Summary

- **2 Ubuntu Server 24.04 nodes**
- **Management Network** (192.168.56.0/24)
  - SSH access
  - Administration & monitoring
- **Production Network** (10.10.10.0/24)
  - Application & storage traffic
- **NFS Shared Storage**
  - Exported only on production network
- **Firewall (UFW)**
  - Enforces traffic separation at the host level


### Environment

- OS: Ubuntu Server 24.04 LTS
- Hypervisor: VirtualBox (macOS host)
- Services: OpenSSH, NFS, UFW

### Networks
- Mgmt (Host-only): 192.168.56.0/24
- Prod (Internal network): 10.10.10.0/24

### IP Plan
| Node | Mgmt IP | Prod IP |
|------|---------|---------|
| DC-Node-01 | 192.168.56.10 | 10.10.10.10 |
| DC-Node-02 | 192.168.56.11 | 10.10.10.11 |

---

## Node Roles

| Node | Role |
|-----|-----|
| DC-Node-01 | Infrastructure / NFS Storage Server |
| DC-Node-02 | Client / Compute Node |



## Services Implemented
- SSH remote administration (Mgmt only)
- NFS shared storage (Prod only)
- Baseline health checks and service validation
- Incident simulations + recovery documentation

---
# Key Implementations

### Networking
- Dual NIC configuration per server
- Static IP addressing
- Clear separation of management and production traffic
- SSH bound to management network only

### Security
- SSH restricted by interface and firewall rules
- Production network explicitly blocked from SSH
- Defense-in-depth using service binding + firewalling

### Storage
- NFS server deployed on production network only
- Export restricted to production subnet
- Persistent NFS mounts using `/etc/fstab`
- `_netdev` option used for safe boot behavior

### Reliability & Operations
- Services validated after reboot
- Controlled failure simulations (service outage, permissions)
- Recovery procedures tested and documented
- Health checks for CPU, memory, disk, network, and services


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
## Documentation Structure

- `docs/`
  - Architecture, procedures, troubleshooting, command reference
- `logs/`
  - Build notes (day-by-day)
  - Incident reports with root cause analysis

---

## Config Examples (Sanitized)
These are documentation examples only (no secrets):
- Netplan examples: [configs/network/](configs/network/)
- NFS exports: [configs/services/nfs-exports.example](configs/services/nfs-exports.example)
- SSH config example: [configs/services/sshd_config.example](configs/services/sshd_config.example)

---
# What This Lab Demonstrates

- Real data center networking concepts
- Operational troubleshooting methodology
- Safe configuration practices
- Clear technical documentation
- Readiness for junior data center / IT operations roles

- 
## Author
Guively Noel  
Location: Georgia, USA  
GitHub: guivelynoel  
LinkedIn: 
