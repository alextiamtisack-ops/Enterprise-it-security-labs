# Ubuntu Linux VM + SSH Setup

## VM Specs
- Hypervisor: VirtualBox
- CPU: 2 cores
- RAM: 4 GB
- Disk: 40 GB
- Network: Bridged Adapter

## Linux Version
- Distribution: Ubuntu 22.04 LTS

## Initial Setup
- Ubuntu installed using standard installer
- Unattended installation disabled
- Virtual hard disk created during VM setup
- System rebooted after installation
- Installation ISO removed after reboot

## System Updates
- Package lists updated
- System packages upgraded
- System rebooted after updates

## Accounts Created
- Default User: alex
- Sudo User: itadmin

## SSH Setup
- OpenSSH server installed
- SSH service enabled to start on boot
- SSH service started manually

## Issues Encountered
- VM failed to boot due to missing virtual hard disk
- SSH service active but not accepting connections
- SSH connection refused due to invalid configuration
- SSH connection timed out when using NAT networking

## Fixes Applied
- Recreated VM with a properly attached virtual hard disk
- Identified invalid ListenAddress entry in /etc/ssh/sshd_config
- Commented out invalid ListenAddress line
- Restarted SSH service
- Changed VirtualBox network adapter from NAT to Bridged

## SSH Verification
- SSH confirmed listening on port 22
- Remote SSH connection initiated from Windows host
- SSH host key accepted on first connection
- User authenticated successfully via SSH

## Notes
- SSH configuration errors can prevent services from binding to network interfaces
- NAT networking blocks inbound connections without port forwarding
- Bridged networking allows the VM to behave like a physical machine on the local network
- Troubleshooting steps were documented and verified after fixes
