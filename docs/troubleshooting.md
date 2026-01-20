# Troubleshooting Runbook

## Issue 001: No connectivity on Mgmt NIC
**Checks**
- `ip a`, `ip r`
- Host-only adapter attached in VirtualBox
**Fix**
- Correct adapter type and re-apply netplan

## Issue 002: No connectivity on Prod NIC
**Checks**
- Internal Network name matches ("prod-net") on both VMs
**Fix**
- Reconfigure adapter, re-apply netplan

## Issue 003: SSH works on Mgmt but fails on Prod (Expected)
**Cause**
- SSH is bound to Mgmt IP by design
**Result**
- Confirms segmentation is working

## Issue 004: NFS mount fails
**Checks**
- `systemctl status nfs-server`
- `/etc/exports` correctness
- Client can ping server on Prod IP
**Fix**
- Restart NFS, re-export, re-mount

## Issue 005: Permission denied on shared folder
**Cause**
- Incorrect chmod/chown on /data/shared
**Fix**
- Restore expected permissions, validate write access

