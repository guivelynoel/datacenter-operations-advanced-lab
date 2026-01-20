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
