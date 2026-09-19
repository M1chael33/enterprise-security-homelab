# Corporate Services

## Corporate Ubuntu Server

I built `project-x-corp-svr` at:

```
10.0.0.8
```

I joined it to the CORP domain and configured SSH for remote administration.

## Docker

I installed Docker and verified it by successfully running a test container.

## MailHog

I deployed MailHog with Docker Compose and exposed:

- SMTP on TCP/1025
- Web UI/API on TCP/8025

I tested message delivery and confirmed that my Linux client could retrieve simulated lab email.

## Linux Email Poller

I configured an `email_poller.sh` script on the Linux client to query the MailHog API periodically for the simulated employee mailbox.

This gave me a simple internal email workflow for the phishing portion of the course without using real email infrastructure.

## Security Takeaway

This section helped me understand how normal enterprise services also become part of the attack surface. SSH, web services, email, and authentication all became relevant later during the attack simulation and investigation.
