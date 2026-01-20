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

## Issue 006 — Host-only Network Not Selectable in VirtualBox (macOS)

**Symptoms**
- VM network adapter set to "Host-only Network"
- Adapter Name shows "Not selected"
- "Invalid settings detected" warning appears
- No selectable host-only network in dropdown

**Environment**
- Host OS: macOS
- Hypervisor: VirtualBox (latest)
- Guest OS: Ubuntu Server

**Root Cause**
- No Host-only Network was created at the global VirtualBox level.
- VirtualBox requires a host-only network (e.g., vboxnet0) to exist
  before it can be assigned to a VM adapter.

**Resolution**
1. Open VirtualBox (not VM settings)
2. Navigate to Tools → Network
3. Create a new Host-only Network
4. Return to VM Settings → Network
5. Select the newly created host-only network (vboxnet0)

**Validation**
- "Invalid settings detected" warning disappears
- Host-only network name is selectable
- VM boots successfully with dual NICs
- `ip a` shows two active interfaces

**Prevention**
- Always verify global VirtualBox networks exist
  before assigning VM network adapters.


