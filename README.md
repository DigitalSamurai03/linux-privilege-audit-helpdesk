# linux-privilege-audit-helpdesk
Privilege audit for ubuntu linux
Linux Privilege & Access Audit
Help Desk / IT Support Focused
📌 Overview

This project documents a structured Linux privilege and access audit performed on an Ubuntu system.
The goal is to demonstrate Help Desk–relevant skills such as:

User and group troubleshooting

Sudo access validation

Basic security hardening

Clear documentation and repeatable procedures

This audit reflects real-world tasks commonly handled by Tier 1 / Tier 2 Help Desk and Junior Systems Administrators.

🎯 Objectives

Identify interactive vs system accounts

Validate sudo access and group membership

Detect misconfigurations that could cause security or access issues

Practice safe inspection of system configuration files

Document findings in a clear, repeatable way

🛠️ Environment

OS: Ubuntu Linux (Desktop)

Shell: Bash

User Context: Standard user with sudo privileges

Tools Used: Core Linux utilities (no third-party tools)

🔍 Audit Scope
1️⃣ User Account Enumeration

Listed all local users

Differentiated human users from service accounts

Verified login shells and home directories

Commands:

getent passwd
awk -F: '$3 >= 1000 {print $1,$3,$7}' /etc/passwd

2️⃣ Group & Permission Review

Reviewed privileged groups (sudo, admin)

Verified correct user group membership

Ensured no service accounts had elevated access

Commands:

getent group sudo
getent group admin
groups digital_samurai

3️⃣ Sudo Access Validation

Verified effective sudo permissions per user

Reviewed sudo configuration safely

Checked for insecure patterns such as passwordless sudo

Commands:

sudo -l
sudo visudo -c
sudo grep -R "NOPASSWD" /etc/sudoers /etc/sudoers.d/

4️⃣ Privilege Escalation Risk Awareness

Identified common privilege escalation vectors

Reviewed system configuration for misconfigurations

Applied least-privilege principles

Examples Reviewed:

Overly broad sudo rules

Unauthorized users in sudo group

Insecure service permissions

✅ Findings Summary

Only authorized user had sudo access

No passwordless sudo rules detected

No system or service accounts with elevated privileges

Default Ubuntu sudo configuration confirmed as secure

🔐 Security & Best Practices

Followed read-only inspection of system files

Used visudo to prevent configuration errors

Avoided direct modification of privilege files

Documented steps for repeatability and troubleshooting

📚 Skills Demonstrated

Linux user and permission troubleshooting

Sudo and access control validation

Security-minded system auditing

Command-line proficiency

Technical documentation

🧭 Relevance to Help Desk Roles

This project aligns with common Help Desk responsibilities, including:

Diagnosing permission-related issues

Verifying administrative access

Assisting with account provisioning and deprovisioning

Escalating legitimate security concerns

Following change-control and least-privilege principles

🔗 MITRE ATT&CK Awareness

T1078 – Valid Accounts

T1548 – Abuse Elevation Control Mechanism

(Used for awareness and defensive understanding only.)

📈 Next Steps

Automate checks with a Bash script

Add SSH access auditing

Expand to multi-user systems

Test on Ubuntu Live USB and VM environments

📝 Author

DigitalSamurai
Aspiring Help Desk / IT Support Technician
Focused on Linux fundamentals, troubleshooting, and security best practices
