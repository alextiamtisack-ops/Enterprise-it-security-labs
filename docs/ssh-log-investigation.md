SSH Log Investigation
VM Environment

Host OS: Windows
Guest OS: Ubuntu Linux
Hypervisor: VirtualBox
Network Mode: NAT

Log File Investigated

Authentication logs in Linux are stored in:

/var/log/auth.log

This log records authentication activity including:

SSH login attempts

Successful SSH logins

sudo privilege usage

Commands Used

View authentication log

sudo less /var/log/auth.log

Search for failed SSH login attempts

sudo grep "Failed password" /var/log/auth.log

Search for successful logins

sudo grep "Accepted" /var/log/auth.log

Search for sudo activity

sudo grep "sudo" /var/log/auth.log

Count login attempts by IP address

sudo grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c

Count total failed login attempts

sudo grep "Failed password" /var/log/auth.log | wc -l
Observations

Total failed login attempts detected: 6

Usernames attempted:

admin (3 attempts)

test (3 attempts)

Source IP address:

::1
IP Address Explanation

::1 is the IPv6 loopback address, equivalent to:

127.0.0.1

This means the login attempts originated from the local system, not from an external attacker.

Log Entry Meanings

invalid user
Indicates the username being attempted does not exist on the system.

sshd
The SSH daemon responsible for handling login attempts.

sudo: alex
Indicates that the user alex executed a command with elevated privileges.

Security Analysis

The login attempts originated from the local loopback address (::1), indicating the activity was part of controlled testing rather than an external attack.

However, the log pattern demonstrates how analysts detect brute-force authentication attempts.

Example brute-force pattern:

Failed → Failed → Failed → Failed → Accepted

This pattern indicates that an attacker eventually guessed the correct password.

Skills Demonstrated

Log Analysis
Analyzed Linux authentication logs to identify login attempts.

Command Line Investigation
Used Linux tools such as grep, awk, sort, and uniq to analyze log data.

Authentication Monitoring
Identified repeated login attempts targeting invalid usernames.

Security Event Recognition
Recognized patterns indicating brute-force authentication attempts.

Network Awareness
Identified the loopback IP address ::1 and determined the activity originated locally.

Privilege Activity Analysis
Reviewed sudo logs to understand administrative command usage.

Security Lessons

Monitor authentication logs regularly

Identify repeated login attempts from the same IP address

Use SSH key authentication instead of passwords

Disable root SSH login

Implement intrusion prevention tools such as fail2ban
