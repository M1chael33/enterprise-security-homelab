# Enterprise Security Homelab

## Project Overview

I built this enterprise cybersecurity homelab while completing **Project Security Enterprise 101**. My goal was to understand how a small enterprise environment is built, administered, attacked, monitored, and investigated from end to end.

I used the course as a full project rather than as isolated exercises. I built the network and servers, configured Windows and Linux systems, deployed defensive monitoring, created a deliberately vulnerable environment, simulated attacker activity, and then investigated that activity in Wazuh from the defender perspective.

> **Lab safety:** All offensive activity documented in this repository was performed only inside my isolated, authorized homelab against systems I owned and configured for training.

## Environment

| System | Role | Lab Address |
|---|---|---|
| `project-x-dc` | Windows Server 2025 domain controller, DNS, DHCP, IIS | `10.0.0.5` |
| `project-x-corp-svr` | Ubuntu corporate server, Docker, MailHog | `10.0.0.8` |
| `project-x-sec-box` | Ubuntu security server running Wazuh | `10.0.0.10` |
| `project-x-attacker` | Kali Linux attacker workstation | `10.0.0.50` |
| `project-x-win-client` | Windows 11 domain workstation | `10.0.0.100` |
| `project-x-linux-client` | Ubuntu domain workstation | `10.0.0.101` |

I configured the Active Directory domain:

```
corp.project-x-dc.com
```

and used an isolated VirtualBox NAT Network on:

```
10.0.0.0/24
```

## What I Practiced

- Active Directory Domain Services
- DNS and DHCP
- Windows Server administration
- Windows 11 administration
- Ubuntu Linux administration
- Linux integration with Active Directory using Samba/Winbind
- VirtualBox networking
- SSH, RDP, WinRM, and SCP
- Docker and MailHog
- Wazuh SIEM/XDR
- File Integrity Monitoring
- Custom Wazuh detection rules
- Wazuh/OpenSearch alert monitors
- Nmap reconnaissance
- Phishing simulation in an isolated lab
- Attack lifecycle analysis
- SOC-style investigation
- Troubleshooting across Windows and Linux

## Project Flow

```text
Build Enterprise Network
        |
        v
Configure AD / DNS / DHCP
        |
        v
Join Windows & Linux Endpoints
        |
        v
Deploy Corporate Services
        |
        v
Deploy Wazuh Monitoring
        |
        v
Create Vulnerable Environment
        |
        v
Simulate Attack
        |
        v
Catch the Attacker
        |
        v
Investigate Activity in Wazuh
```

## Repository Guide

- [Architecture](architecture/README.md)
- [Active Directory & Infrastructure](active-directory/README.md)
- [Corporate Services](corporate-services/README.md)
- [Wazuh SIEM](wazuh-siem/README.md)
- [Vulnerable Environment](vulnerable-environment/README.md)
- [Attack Simulation](attack-simulation/README.md)
- [Catch the Attacker / Wazuh Investigation](catch-the-attacker/README.md)
- [Detection Engineering](detections/README.md)
- [Troubleshooting](troubleshooting/README.md)
- [Lessons Learned](lessons-learned.md)
- [Resume Bullets](career/resume-bullets.md)
- [Interview Talking Points](career/interview-talking-points.md)

## My Biggest Takeaway

The most valuable part of this project was being able to generate attacker activity myself and then investigate the same activity in Wazuh.

That connected infrastructure, networking, Windows/Linux administration, attack techniques, logging, detection engineering, and SOC investigation into one project.

## Course Credit

This lab was built while completing **Project Security Enterprise 101**. Project Security provided the course framework. The implementation notes, troubleshooting notes, observations, and explanations in this repository describe my own lab experience and are written in my own words.
