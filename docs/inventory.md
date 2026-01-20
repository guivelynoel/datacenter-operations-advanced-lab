# Inventory

## Host
- Platform: macOS + VirtualBox
- Guest OS: Ubuntu Server (latest)

## Nodes
### DC-Node-01 (Infrastructure / Storage)
- CPU: 2 vCPU
- RAM: 4 GB
- Disk: 40 GB
- NIC1 (Mgmt): 192.168.56.10/24
- NIC2 (Prod): 10.10.10.10/24

### DC-Node-02 (Compute / Client)
- CPU: 2 vCPU
- RAM: 2 GB
- Disk: 40 GB
- NIC1 (Mgmt): 192.168.56.11/24
- NIC2 (Prod): 10.10.10.11/24

## Networks
- Mgmt: Host-only (vboxnet0) 192.168.56.0/24
- Prod: Internal Network "prod-net" 10.10.10.0/24

