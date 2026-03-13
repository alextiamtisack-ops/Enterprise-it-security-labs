# Day 7 — Network Traffic Investigation with tcpdump

## Objective

The objective of this lab was to observe live network traffic and understand how packet captures can reveal network behavior such as service connections and reconnaissance activity.

---

## Tools Used

* Ubuntu Linux
* tcpdump
* SSH
* Nmap

---

## Commands Executed

Check if tcpdump is installed:

```
tcpdump --version
```

Identify network interfaces:

```
ip a
```

Capture SSH traffic on the loopback interface:

```
sudo tcpdump -i lo port 22
```

Generate SSH traffic:

```
ssh localhost
```

Capture general network traffic:

```
sudo tcpdump -i lo -nn
```

Generate reconnaissance traffic:

```
nmap localhost
```

---

## Observations

During the packet capture, tcpdump displayed packets showing communication between localhost addresses. The output included source and destination ports along with TCP flags.

Example packet structure observed:

```
127.0.0.1.55584 > 127.0.0.1.22
```

This indicates:

* `127.0.0.1` is the localhost address
* `55584` is a temporary client port
* `22` is the SSH service port

When SSH was executed, many packets appeared between localhost addresses using port 22.

When running an Nmap scan, many packets appeared targeting different destination ports very quickly.

---

## Security Analysis

Packet captures help defenders understand how systems communicate on a network. By observing the destination ports in tcpdump output, it is possible to identify patterns that indicate reconnaissance activity.

For example, when many packets are sent to multiple destination ports in a short time, this behavior can indicate a port scan. Port scanning is commonly used by attackers to identify open services on a system.

Monitoring packet patterns allows security analysts to detect early stages of an attack before exploitation occurs.

---

## Lessons Learned

This lab demonstrated how tcpdump can be used to capture and analyze live network traffic. It showed how SSH connections appear in packet captures and how reconnaissance tools like Nmap generate recognizable traffic patterns.

Understanding packet structure and network behavior is important for detecting malicious activity and investigating security incidents.

---

## Key Security Concepts Learned

* Packet capture
* Source vs destination ports
* Loopback network traffic
* Port scanning detection
* Network reconnaissance behavior
