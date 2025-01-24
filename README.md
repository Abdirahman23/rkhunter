# Rootkit Hunter (rkhunter) 
Overview
Rootkit Hunter (rkhunter) is a security tool for Unix-based systems that scans for rootkits, backdoors, and other potential security vulnerabilities. It works by comparing file properties, looking for common rootkit signatures, and detecting unusual behavior or configurations.

# Features
Detects rootkits, backdoors, and malware.
Scans system files, hidden files, and permissions.
Checks for anomalies in binaries, configuration files, and libraries.
Performs network tests for suspicious activities.
Generates detailed logs and reports.

# Installation
On Debian/Ubuntu:
sudo apt update
sudo apt install rkhunter

# On Red Hat/CentOS:

sudo yum install epel-release
sudo yum install rkhunter

# Basic Usage
# 1. Update rkhunter Databases
Before running scans, update the detection database:
sudo rkhunter --update

# 2. Set Baseline for File Properties
Run this command after legitimate system updates to prevent false positives:
sudo rkhunter --propupd

# 3. Run a Scan
Perform a system scan:
sudo rkhunter --check

#4. Review Logs
Scan results are saved in /var/log/rkhunter.log. To view the log:
sudo less /var/log/rkhunter.log

# Automating Scans
Automate rkhunter scans using cron jobs. Example (daily at midnight):
0 0 * * * /usr/bin/rkhunter --check --cronjob --report-warnings-only | mail -s "rkhunter Report" your-email@example.com

# Troubleshooting
Warnings: Investigate any warnings in the log file.
False Positives: If legitimate changes trigger warnings, update the file properties database:
sudo rkhunter --propupd
Logs Not Rotating: Use log rotation tools to manage /var/log/rkhunter.log.

#Common Commands

# Update the detection rules:
sudo rkhunter --update
Perform a full system scan:
sudo rkhunter --check

#Quiet mode scan (for automation):
sudo rkhunter --check --quiet

# Best Practices
Regularly update rkhunter and system packages.
Investigate all warnings, even if they seem benign.
Only run --propupd if you are sure the system is clean.
Monitor logs for unusual patterns.
