# Troubleshooting Notes

A large part of this project was troubleshooting. I documented these examples because they show how I approached technical problems instead of only following the successful path.

## Wazuh Installation

I encountered a partially installed Wazuh manager where some processes and ports existed but required manager files were missing.

I checked package state, running processes, listening ports, and the installation directory. I cleaned the broken deployment, reinstalled Wazuh, and verified that the dashboard and endpoint agents worked afterward.

## DNS and Active Directory

I saw firsthand how dependent Active Directory is on DNS.

When DNS was wrong or the domain controller was unavailable, authentication and domain-related operations failed in ways that initially looked unrelated.

I learned to check:

- IP addressing
- gateway
- DNS server
- name resolution
- service reachability
- time synchronization

before assuming credentials were the problem.

## SSH

I troubleshot:

- inactive SSH services
- connection refused
- authentication behavior
- password authentication
- root-login settings
- port 22 reachability

Tools and commands I used included:

```bash
systemctl status ssh
ss -lnt
nc -vz <host> 22
ssh -v <user>@<host>
```

## Apache / PHP

When Apache showed the default page instead of the lab phishing page, I checked the document root.

When the form returned a not-found error, I inspected the HTML form action and found that it expected `process.php`, which had not yet been placed in the web root.

## General Troubleshooting Method

```text
Reproduce problem
      |
      v
Check connectivity
      |
      v
Check service status
      |
      v
Check ports
      |
      v
Inspect logs/configuration
      |
      v
Change one thing
      |
      v
Retest
```

Troubleshooting became one of the most valuable skills I practiced in the course.
