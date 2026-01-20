# Incident Log — Data Center Operations Lab

This document records operational issues encountered during lab setup,
including root cause analysis, resolution steps, and lessons learned.
Some incidents were documented retroactively to ensure accuracy and completeness.

---

## Incident 001 — Host-only Network Missing (VirtualBox macOS)

**Impact**
VM could not be configured with Host-only Network; adapter name unavailable.

**Root Cause**
No Host-only Network existed at the VirtualBox global level.

**Resolution**
Created Host-only Network via VirtualBox Tools → Network.

**Validation**
Host-only network selectable as vboxnet0; VM settings validated.

**Lesson Learned**
Always verify global network objects before VM assignment.

---

## Incident 002 — Invalid VM Network Configuration

**Impact**
VirtualBox displayed "Invalid settings detected" and blocked VM startup.

**Root Cause**
Host-only Network selected without specifying a network name.

**Resolution**
Selected vboxnet0 after creating Host-only Network.

**Validation**
Invalid settings warning cleared; VM booted successfully.

**Lesson Learned**
VirtualBox requires explicit network selection on macOS.

---

## Incident 003 — Expected Netplan File Not Found

**Impact**
Static IP configuration could not proceed using assumed filename.

**Root Cause**
Ubuntu Server generated a different Netplan configuration file
based on installer and OS version.

**Resolution**
Listed `/etc/netplan` directory and edited the existing YAML file.

**Validation**
Static IPs applied successfully using Netplan.

**Lesson Learned**
Never assume Netplan filenames; always inspect the directory.

---

## Incident 004 — SSH Isolation Configuration Ignored

**Impact**
SSH continued listening on all interfaces despite ListenAddress settings.

**Root Cause**
OpenSSH configuration overridden by systemd socket activation.

**Resolution**
Investigated sshd_config.d overrides and systemd behavior.

**Validation**
Issue narrowed down to socket activation control.

**Lesson Learned**
Modern Ubuntu versions may not apply service changes
through traditional config files alone.

---

## Incident 005 — SSH Socket Activation Prevented Interface Binding

**Impact**
SSH remained bound to 0.0.0.0:22 even after configuration updates.

**Root Cause**
OpenSSH managed by systemd socket activation (`ssh.socket`).

**Resolution**
Reloaded systemd units and restarted ssh.socket:
- `systemctl daemon-reload`
- `systemctl restart ssh.socket`

**Validation**
SSH bound only to management IP as verified by `ss -tulpn`.

**Lesson Learned**
For socket-activated services, restarting the service alone
is insufficient; the socket must be reloaded.

---

## Incident 008 — No Internet Connectivity for Package Updates

**Impact**:
Unable to update packages using apt.

**Root Cause:**
No default route to the internet due to isolated network design.

**Resolution**:
Temporarily enabled NAT adapter for maintenance operations.

**Lesson Learned**:
Maintenance access should be temporary and controlled.

## Incident 009 — Misinterpreted nfs-server Service State

Impact:
Initial concern about service availability.

Root Cause:
Misunderstanding of systemd oneshot service behavior.

Resolution:
Validated NFS operation via kernel threads and client access.

Lesson Learned:
Not all active services maintain a running process.

## Incident 010 — NFS Permission Misconfiguration

Impact:
Client unable to write to shared storage.

Root Cause:
Incorrect directory permissions.

Resolution:
Restored correct ownership and permissions.

Lesson Learned:
Permissions are critical for shared storage reliability.

