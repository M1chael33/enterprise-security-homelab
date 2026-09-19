# Attack Simulation

> All activity documented here was performed only against my own isolated Enterprise 101 lab.

I used `project-x-attacker`, a Kali Linux workstation, to simulate the attacker side of the course.

## Attack Lifecycle

I worked through the course flow:

1. Reconnaissance
2. Initial Access
3. Phishing / Lure
4. Lateral Movement
5. Privilege Escalation
6. Data Exfiltration
7. Persistence
8. Defensive Investigation

## Reconnaissance

I used Nmap and other basic enumeration techniques to identify hosts, ports, and services inside the lab.

This helped me understand what an attacker could learn before authenticating.

## Initial Access

I tested the deliberately vulnerable remote services and credentials configured for the lab.

The main lesson was how weak authentication and exposed administrative services can turn normal infrastructure into a path for compromise.

## Phishing Simulation

I configured Apache on Kali and hosted the training phishing page locally.

During setup I troubleshot:

- Apache showing the default page
- locating the correct lab `index.html`
- identifying the HTML form action
- discovering the missing `process.php`
- placing the handler in the web root
- validating the simulated credential workflow

I used only dummy lab credentials and did not target real users.

## Lateral Movement and Privilege Escalation

I followed the course scenario to understand how access to one system can lead to access on another and how credentials, administrative protocols, and privilege boundaries affect lateral movement.

## Data Exfiltration

I used the lab's simulated `secrets.txt` file as the target data and practiced transferring it to the attacker system with SCP.

The technique was intentionally simple, but it created a clear event I could later compare against my Wazuh telemetry.

## Persistence

I completed the persistence portion to understand why an attacker may try to maintain access after compromise.

## Defender Handoff

After completing the attack portion, I switched roles and investigated the activity using Wazuh.

See [Catch the Attacker](../catch-the-attacker/README.md).
