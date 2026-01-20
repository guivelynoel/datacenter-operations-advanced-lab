
# Network Design

## Objective
Separate administration from production/service traffic using dual NICs.

## Networks
### Mgmt Network (Host-only)
- Subnet: 192.168.56.0/24
- Purpose: SSH administration only
- Notes: Predictable access from the macOS host

### Prod Network (Internal Network: "prod-net")
- Subnet: 10.10.10.0/24
- Purpose: NFS/storage and server-to-server traffic
- Notes: Simulates east-west traffic inside a rack/cluster

## Validation Tests
- Ping Mgmt:
  - DC-Node-02 -> 192.168.56.10
- Ping Prod:
  - DC-Node-02 -> 10.10.10.10
- SSH should work only on Mgmt IPs
