# Procedures (SOP)

## SOP-001: Base Install + Updates
- Install Ubuntu Server
- Enable OpenSSH during install
- Update packages and reboot

## SOP-002: Configure Dual NIC Static IP (Netplan)
- Identify interfaces with `ip a`
- Apply static IPs for Mgmt and Prod NICs
- Use `netplan try` then `netplan apply`
- Fix permissions with `chmod 600 /etc/netplan/*.yaml`

## SOP-003: SSH Mgmt Binding
- Configure ListenAddress to Mgmt IP
- Disable root login
- Restart ssh and validate connectivity

## SOP-004: Deploy NFS on Prod Network
- Install NFS server on DC-Node-01
- Export /data/shared to 10.10.10.0/24
- Mount from DC-Node-02 and validate file operations

## SOP-005: Persistent NFS Mount

- Configured NFS mount using /etc/fstab
- Used _netdev to ensure safe boot behavior
- Validated with mount -a and reboot test

## SOP-006: Firewall Enforcement

- Enabled UFW
- Allowed SSH only on management network
- Restricted NFS to production network
- Validated rules with ufw status


## SOP-007: Health Checks
- CPU: `uptime`
- Memory: `free -h`
- Disk: `df -h`
- Services: `systemctl status ssh nfs-server`
  

