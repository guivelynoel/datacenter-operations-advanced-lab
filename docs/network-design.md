
# Network Design

## Objective
Separate administration from production/service traffic using dual NICs.


## VirtualBox Configuration (macOS)

- Adapter 1: Host-only Network (Management)
- Adapter 2: Internal Network "prod-net" (Production)
- Deprecated Host-only Adapter mode not used
-When using Host-only Network on macOS, a specific network
        (e.g., vboxnet0) must be selected. Leaving the name unset
        results in invalid VM settings.
    

        


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
