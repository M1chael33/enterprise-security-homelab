# Lab Architecture

I built the lab in VirtualBox using an isolated NAT Network named `project-x-network`.

## Network Design

```text
Network: 10.0.0.0/24
Gateway: 10.0.0.1

                    +----------------------+
                    | project-x-dc         |
                    | 10.0.0.5             |
                    | AD / DNS / DHCP      |
                    +----------+-----------+
                               |
          +--------------------+--------------------+
          |                    |                    |
+---------v---------+ +--------v---------+ +--------v---------+
| Windows Client   | | Linux Client     | | Corp Server      |
| 10.0.0.100       | | 10.0.0.101       | | 10.0.0.8         |
+------------------+ +------------------+ +------------------+
                                                     |
                                            Docker / MailHog

+------------------+                       +------------------+
| Security Server  |                       | Kali Attacker    |
| 10.0.0.10        |                       | 10.0.0.50        |
| Wazuh            |                       | Attack testing   |
+------------------+                       +------------------+
```

## Why I Designed It This Way

I used dedicated systems for the domain controller, corporate services, security monitoring, endpoints, and attacker workstation so I could understand how separate enterprise roles interact.

I used static addressing for the main servers so DNS, Wazuh, SSH, and remote administration had predictable destinations.

I kept the environment isolated from production systems. All offensive testing remained inside this lab.
