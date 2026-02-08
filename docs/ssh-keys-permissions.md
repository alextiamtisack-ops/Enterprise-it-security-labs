# Day 3 — SSH Key Authentication and Linux Permissions

## Goal
- Configure secure SSH access using key-based authentication
- Disable password-based SSH login
- Understand basic Linux file permissions
- Identify authentication-related log files

## SSH Key Setup (Windows Host)
- SSH key pair generated using ssh-keygen
- ED25519 key type used
- Key files stored in ~/.ssh directory on Windows host
- Public key identified as id_ed25519.pub

## SSH Key Installation (Linux VM)
- Logged into Ubuntu VM via VirtualBox console
- Created SSH directory manually
- Correct permissions applied to SSH directory
- Public key manually added to authorized_keys file

Commands Used:
- mkdir /home/alex/.ssh
- chmod 700 /home/alex/.ssh
- nano /home/alex/.ssh/authorized_keys
- chmod 600 /home/alex/.ssh/authorized_keys

## SSH Configuration
- Password authentication disabled
- Root login disabled
- SSH service restarted after configuration changes

Configuration File:
- /etc/ssh/sshd_config

## SSH Verification
- SSH connection tested from Windows host
- Successful login without password prompt
- SSH service confirmed running and active

## Linux Permissions
- Reviewed file permission structure (rwx)
- Verified correct permissions on SSH-related files
- Ownership and permissions confirmed to allow SSH key authentication

## Logs
- Authentication logs identified in /var/log/auth.log
- SSH login activity observed using log output

## Issues Encountered
- Password SSH disabled before SSH key was installed
- SSH access temporarily blocked due to authentication restrictions
- SSH key copy failed due to disabled password authentication

## Fixes Applied
- Accessed system using VM console
- Manually installed SSH public key
- Corrected file permissions and ownership
- Restarted SSH service

## Notes
- SSH keys provide stronger security than passwords
- Console access is critical for recovery when SSH access is locked
- Proper file permissions are required for SSH key authentication
- Troubleshooting steps were documented and verified after fixes
