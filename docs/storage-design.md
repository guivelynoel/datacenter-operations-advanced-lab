# Storage Design (NFS on Prod Network)

## Goal
Provide shared storage from DC-Node-01 to DC-Node-02 using NFS,
restricted to the production subnet.

## Server (DC-Node-01)
- Export path: /data/shared
- Allowed subnet: 10.10.10.0/24

## Client (DC-Node-02)
- Mount point: /mnt/shared
- Mount target: 10.10.10.10:/data/shared

## Validation
- Create a test file from client and confirm visibility on server
- Simulate service outage and recover (incident documentation)

## Implementation

- NFS server hosted on DC-Node-01
- Export restricted to production subnet (10.10.10.0/24)
- Clients mount using production IP only

## Validation

- File creation from client visible on server
- Mount attempts via management network fail (expected)
