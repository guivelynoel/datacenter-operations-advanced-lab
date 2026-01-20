# Security Controls

## SSH (Mgmt Only)
- SSH is bound to the Mgmt IP using ListenAddress.
- Root login is disabled.

## Why
- Keeps administration access separate from service traffic.
- Matches real operational security practices.

## Validation
- SSH success: ssh admin@192.168.56.10
- SSH should fail on Prod IP: ssh admin@10.10.10.10 (expected)

## SSH Socket Activation (Ubuntu 24.04)

On Ubuntu 24.04, OpenSSH uses systemd socket activation.
As a result, SSH listening behavior is controlled by `ssh.socket`.

When modifying SSH binding or ListenAddress settings:
- `systemctl daemon-reload` must be executed
- `ssh.socket` must be restarted

This ensures SSH applies updated interface restrictions.
