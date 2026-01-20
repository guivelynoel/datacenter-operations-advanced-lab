# Architecture Explanation

## Why Two Networks?
Real data centers commonly separate:
- **Management traffic** (admin/SSH, break-glass access)
- **Production traffic** (apps, storage, east-west communication)

This reduces risk, improves organization, and makes troubleshooting easier.

## Traffic Rules in This Lab
- SSH binds to Mgmt IP only:
  - DC-Node-01: 192.168.56.10
  - DC-Node-02: 192.168.56.11
- NFS runs only on the Prod network:
  - Server: 10.10.10.10
  - Client: 10.10.10.11

## What This Demonstrates
- Multi-NIC server thinking
- Network segmentation
- Service placement based on traffic type
- Operational troubleshooting and incident handling

