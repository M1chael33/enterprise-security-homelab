# Vulnerable Environment

After building the normal enterprise environment, I intentionally configured conditions that could be exploited inside the training lab.

The goal was to understand what insecure configurations look like from both attacker and defender perspectives.

## Simulated Sensitive Data

I created a simulated sensitive file on the domain controller:

```
C:\Users\Administrator\Documents\ProductionFiles\secrets.txt
```

I later used this file for File Integrity Monitoring, alerting, and the data-exfiltration portion of the course.

## Remote Services

I configured and tested lab services including:

- SSH
- RDP
- WinRM
- SCP

This helped me see how authentication settings, administrative services, and system configuration affect attack surface.

## Baseline Monitoring

Before moving into the attack simulation, I verified that Wazuh was receiving endpoint telemetry and that my sensitive-file detection worked.

That gave me a known-good defensive baseline before I started generating attacker activity.
