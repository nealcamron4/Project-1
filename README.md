## Author
Camron Neal

## Overview
This repository documents a comprehensive Linux system hardening project performed over the course of three days. The goal was to enhance system security through user management, service configuration, file permission settings, auditing, and automation via shell scripting.

---

 Day 1 - System Information & User Management
✅ Part 1: System Information & OS Backup
Collected system info: hostname, OS version, memory, uptime.

Backed up OS using:

bash
Copy
Edit
tar -cvpzf /baker_street_backup.tar.gz --exclude=/proc --exclude=/tmp --exclude=/mnt --exclude=/sys --exclude=/dev --exclude=/run /
✅ Part 2: User Account Management
Removed terminated users: userdel -r username

Locked users on leave: passwd -l username

Unlocked active users: passwd -u username

✅ Part 3: Password Policies
Installed libpam-pwquality and updated /etc/pam.d/common-password.

Forced password updates via pam-auth-update --force.

✅ Part 4: Sudo Permissions
Granted full sudo to sherlock.

Limited sudo access to watson and mycroft for specific scripts via visudo.

✅ Part 5: File Permissions
Removed world (o=rwx) permissions from /home.

📅 Day 2 - SSH & Package Hardening
✅ Part 1: SSH Configuration
Disabled root login and empty passwords.

Ensured only port 22 is used and set SSH to Protocol 2.

✅ Part 2: Package Management
Identified insecure packages (telnet, rsh-client) and removed them.

Installed secure tools: ufw, lynis, tripwire.

✅ Part 3: Services Audit
Listed and logged all running services.

Removed unnecessary services like MySQL and Samba.

✅ Part 4: Logging Configuration
Set persistent logs and max usage in /etc/systemd/journald.conf.

Updated log rotation in /etc/logrotate.conf (daily, every 7 days).

📅 Day 3 - Scripting
✅ Part 1: hardening_script1.sh
Automates:

System info logging

OS backup

Sudoers file check

World permission audit

Departmental file permission fixes

✅ Part 2: hardening_script2.sh
Automates:

SSH config checks

System updates

Log file audits (journald.conf, logrotate.conf)

📂 Files
hardening_script1.sh: Automates Day 1 tasks.

hardening_script2.sh: Automates Day 2 logging and checks.

package_list.txt, service_list.txt: Output files generated during the process.

🛠️ Requirements
Linux system with sudo access

libpam-pwquality, ufw, lynis, tripwire packages

