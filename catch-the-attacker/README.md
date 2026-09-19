# Catch the Attacker — Wazuh Investigation

This was the final part of the Enterprise 101 project and one of the most useful sections for me.

After I completed the attack simulation, I switched from the attacker perspective to the defender perspective and investigated the activity in Wazuh.

## Investigation Goal

I approached the investigation like a SOC analyst and focused on questions such as:

- Which endpoint generated the event?
- What happened?
- When did it happen?
- Which Wazuh rule detected it?
- What severity was assigned?
- What events happened immediately before and after it?
- Could I correlate the telemetry with actions from my attack simulation?

## Threat Hunting

I used Wazuh Threat Hunting to search through endpoint events and inspect fields including:

- agent name
- agent IP
- timestamp
- decoder
- rule ID
- rule description
- event location
- file metadata
- hashes
- severity

Because I had generated the attack activity myself, I could compare the telemetry directly against the known attack timeline.

## File Integrity Investigation

A strong example was my investigation of the monitored `secrets.txt` file.

When the file changed, Wazuh produced an integrity event showing information such as:

- affected file
- modification time
- old and new file size
- MD5 changes
- SHA-1 changes
- SHA-256 changes

I confirmed that my custom rule fired:

```
Rule 100002 - File Accessed
```

I then reviewed the monitor:

```
File Accessed Trigger
```

and verified the alert history. I learned that an alert showing as `Completed` did not mean the detection failed; it meant the trigger condition had previously been met and the alert period later ended.

## My Investigation Workflow

```text
Alert detected
     |
     v
Identify endpoint
     |
     v
Check timestamp
     |
     v
Inspect rule and event details
     |
     v
Search surrounding events
     |
     v
Compare against attack timeline
     |
     v
Determine what happened
```

## SOC Skills I Practiced

- alert triage
- threat hunting
- event searching
- endpoint telemetry analysis
- File Integrity Monitoring
- custom rule validation
- alert timeline analysis
- timestamp correlation
- Windows/Linux event investigation
- connecting detections to underlying activity

## How I Explain This to an Employer

> I built a virtual enterprise network, attacked it from a dedicated Kali system, and then switched to the defender side and investigated the activity in Wazuh. I configured File Integrity Monitoring for a sensitive directory, wrote a custom Wazuh rule, created an alert monitor, generated test activity, and validated the resulting alerts using endpoint telemetry and event timelines.

That is the part of the project I would emphasize most when discussing SOC or Security Analyst roles.
