# brute-force-detection-lab
SSH brute-force detection lab: generating failed logins and analyzing auth.log on Ubuntu
# 🔐 Brute Force Detection Lab

Detecting failed SSH login attempts by analyzing Linux authentication logs.

![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![SSH](https://img.shields.io/badge/Service-SSH-2C5364?style=flat-square)
![MITRE](https://img.shields.io/badge/MITRE-T1110-red?style=flat-square)

## 🎯 Objective
Generate failed SSH logins against my own Ubuntu VM and detect them in `/var/log/auth.log`, practicing the log-analysis skills a SOC analyst uses.

## 🧪 Lab Setup
| Role | Machine |
|---|---|
| Attacker | Kali Linux (VMware) |
| Target | Ubuntu (ubuntu-soc-target) with sshd |

All testing was done on my own VMs.

## 🔍 Method
1. From Kali, attempted SSH login with 3 wrong passwords.
2. On Ubuntu, searched the authentication log:
```bash
   sudo grep "Failed password" /var/log/auth.log | tail -n 10
```

## 📌 Findings
- 3 failed password attempts for user `soc` within about 63 seconds
- All from one source IP, inside a single SSH connection
- Each attempt recorded with timestamp, username, IP and port


## 🛡️ Recommendations
- Install fail2ban to ban IPs after repeated failures
- Use key-based SSH authentication and disable password login
- Alert on repeated `Failed password` events



## 🧰 Skills Demonstrated
Linux log analysis · grep · SSH security · Brute-force detection · MITRE ATT&CK mapping · Incident reporting
