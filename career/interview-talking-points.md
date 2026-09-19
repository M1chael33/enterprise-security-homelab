# Interview Talking Points

## Tell Me About a Cybersecurity Project

> I built an enterprise cybersecurity homelab based on Project Security Enterprise 101. I created a Windows Active Directory domain with Windows and Linux endpoints, a corporate Ubuntu server, a dedicated Wazuh security server, and a Kali attacker workstation.
>
> After building the environment, I created a vulnerable scenario and simulated attacker activity including reconnaissance, phishing, remote access, lateral movement, privilege escalation, and data exfiltration.
>
> The part I found most valuable was switching back to the defender side. I used Wazuh to investigate the activity I had generated, configured File Integrity Monitoring for a sensitive directory, wrote a custom Wazuh detection rule, created an alert monitor, and validated the resulting alerts against the attack timeline.

## What Did You Personally Configure?

I can discuss:

- Active Directory
- DNS and DHCP
- Windows and Linux domain membership
- Samba/Winbind
- SSH and remote administration
- Docker
- MailHog
- Wazuh deployment
- endpoint agents
- File Integrity Monitoring
- custom Wazuh rules
- alert monitors
- Kali attack workstation
- Apache/PHP phishing simulation
- attacker and defender workflows

## Tell Me About a Problem You Solved

A strong example is my Wazuh deployment:

> I encountered a partial Wazuh installation where processes and ports existed but required files were missing. I checked package state, processes, open ports, and installation files, cleaned the broken deployment, reinstalled it, and verified that the dashboard and endpoint agents were functioning afterward.

Another example is the phishing page:

> Apache loaded successfully, but the phishing form returned a not-found error. I inspected the HTML form action, discovered that it depended on process.php, located the missing handler, placed it in the correct document root, and retested the application.

## How Did You Catch the Attacker?

> I used Wazuh to investigate the activity after completing the attack simulation. I searched endpoint events, reviewed agent and rule information, correlated timestamps, and examined File Integrity Monitoring events. One of my custom detections watched a sensitive file and generated Rule 100002, which I tied to an alert monitor. Because I had generated the attack activity myself, I could validate the telemetry against the known attack timeline.

## What Would I Improve Next?

I would continue expanding the project with:

- more endpoint telemetry
- additional custom detections
- MITRE ATT&CK mappings
- investigation playbooks
- network IDS telemetry
- alert enrichment
- repeatable deployment automation
