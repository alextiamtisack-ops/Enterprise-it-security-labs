# Network Port Scanning Investigation

## VM Environment

* Host OS: Windows
* Guest OS: Ubuntu Linux
* Hypervisor: VirtualBox
* Network Mode: NAT

## Objective

* Investigate open network ports on the system
* Understand how attackers discover services
* Learn how port scanning reveals system attack surfaces

## Tool Used

* Network scanning performed using **Nmap**

## Commands Used

Install Nmap

```bash
sudo apt install nmap
```

Run basic scan

```bash
nmap localhost
```

Run SYN scan (requires root privileges)

```bash
sudo nmap -sS localhost
```

## Observations

* Nmap scanned the most common 1000 TCP ports
* Two ports were identified as open
* Remaining ports were reported as closed

Example scan result:

```
22/tcp   open   ssh
631/tcp  open   ipp
```

## Port Analysis

### Port 22

* Service: SSH (Secure Shell)

Purpose:

* Allows secure remote login and system administration.

Security Relevance:

* Attackers commonly target SSH with brute-force login attempts.
* Weak passwords or misconfigured authentication could allow unauthorized access.

### Port 631

* Service: IPP (Internet Printing Protocol)
* Associated Software: CUPS printing system

Purpose:

* Manages printing services and printer configuration.

Security Relevance:

* This service was bound to localhost and not externally accessible.
* Local services may still present risks if attackers gain system access.

## Key Concepts Learned

### Port Scanning

Port scanning allows attackers or defenders to discover which services are running on a system.

### Port States

Ports typically appear in one of three states:

```
open
closed
filtered
```

### Attack Surface

Every open port represents a potential entry point attackers may attempt to exploit.

### Local vs External Scanning

* Local scans reveal all services running on the system.
* External scans only detect services exposed to the network.

## Security Lessons

* Attackers often begin with network reconnaissance.
* Port scanning helps identify potential targets.
* Even systems with few open ports may still contain vulnerabilities.
* Monitoring and securing exposed services reduces attack risk.

## Notes

* Port scanning is commonly used by both security analysts and attackers.
* Understanding how services respond to scans helps defenders recognize reconnaissance activity.
* Network reconnaissance is often the first step in a cyber attack.
