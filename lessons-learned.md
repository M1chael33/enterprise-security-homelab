# Lessons Learned

## Infrastructure Comes First

Building the environment showed me that cybersecurity depends heavily on system administration. DNS, DHCP, Active Directory, authentication, SSH, RDP, WinRM, Linux services, and networking all affected the security exercises.

## DNS Is Critical to Active Directory

I learned quickly that incorrect DNS configuration can create failures that look like authentication or application problems.

## Logs Make More Sense When I Generate the Activity

The most useful detections were the ones tied to actions I had personally performed.

Instead of memorizing what a Wazuh event meant, I could generate an action, observe the event, and understand which fields represented the behavior.

## A SIEM Requires Engineering

Installing Wazuh was only the beginning.

I had to:

1. connect endpoints,
2. collect telemetry,
3. configure monitoring,
4. create a custom rule,
5. generate test behavior,
6. validate the rule,
7. create an alert monitor,
8. investigate the alert.

That gave me a much better understanding of what SIEM work actually looks like.

## Attacker Knowledge Helps Defense

Working through reconnaissance, initial access, lateral movement, privilege escalation, exfiltration, and persistence helped me understand why certain events matter to defenders.

## Troubleshooting Is a Security Skill

Some of my best learning happened when the lab broke. I had to troubleshoot networking, DNS, SSH, permissions, package state, Wazuh, Apache, and remote access.

That made me more comfortable isolating problems instead of immediately rebuilding systems.
