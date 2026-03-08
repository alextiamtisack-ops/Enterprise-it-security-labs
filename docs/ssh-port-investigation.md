# SSH Port Investigation

## VM Environment

* Host OS: Windows
* Guest OS: Ubuntu Linux
* Hypervisor: VirtualBox
* Network Mode: NAT

## Objective

* Investigate which services are listening on network ports
* Understand the system's network attack surface
* Identify which services are reachable from the network

## Command Used

* Command executed to view listening network services

```
ss -tuln
```

## Listening Services Observed

* Multiple listening sockets detected
* Key services identified through port numbers

Example output:

```
LISTEN 0 4096 127.0.0.1:631
LISTEN 0 4096 0.0.0.0:22
```

## Port Analysis

### SSH Service

* Port: 22
* Address: 0.0.0.0
* Service: SSH (Secure Shell)

Explanation:

* SSH allows secure remote login and administration
* Listening on `0.0.0.0` means the service accepts connections on all network interfaces

Security Implication:

* SSH services are commonly targeted by brute-force login attacks
* Attackers attempt multiple username and password combinations to gain access

### Printing Service

* Port: 631
* Address: 127.0.0.1
* Service: CUPS (Common Unix Printing System)

Explanation:

* Used for printer management and print job handling
* Bound to `127.0.0.1`, meaning it only accepts connections from the local system

Security Implication:

* Not reachable from external systems
* Minimal remote attack risk

## Network Address Interpretation

* `127.0.0.1` → Localhost only (local system access)
* `0.0.0.0` → Listening on all network interfaces

Understanding these addresses helps determine which services are **externally reachable**.

## Attack Surface Analysis

* Only one externally reachable service identified: SSH (port 22)
* Limited number of exposed services indicates a **small attack surface**

Potential attacker actions if SSH is reachable:

* Port scanning
* Brute-force login attempts
* Credential guessing

## Skills Demonstrated

* Network service enumeration
* Port and service identification
* Attack surface analysis
* Security interpretation of listening network services
* Understanding network interface binding

## Security Lessons

* Every open port represents a potential entry point for attackers
* Services bound to localhost are not externally accessible
* Minimizing exposed services reduces system attack surface
* SSH services should be protected using strong authentication methods (such as SSH keys)

## Notes

* Network reconnaissance is often the first step attackers perform
* Tools like `ss` help defenders understand which services are exposed
* Monitoring listening services is important for maintaining a secure system
