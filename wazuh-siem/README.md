# Wazuh SIEM / XDR

## Security Server

I deployed Wazuh on `project-x-sec-box` at:

```
10.0.0.10
```

I used the Wazuh dashboard to monitor agents, search endpoint events, review alerts, and validate detections.

## Endpoint Monitoring

I deployed Wazuh agents to lab endpoints, including the Windows domain controller, and verified that telemetry was reaching the manager.

## File Integrity Monitoring

I configured Wazuh File Integrity Monitoring for:

```
C:\Users\Administrator\Documents\ProductionFiles
```

The monitored directory contained a simulated sensitive file:

```
secrets.txt
```

After modifying the file, I confirmed that Wazuh generated a real-time syscheck integrity event.

## Custom Detection Rule

I created this custom Wazuh rule:

```xml
<rule id="100002" level="10">
  <if_sid>550</if_sid>
  <field name="file">secrets.txt</field>
  <description>File Accessed</description>
</rule>
```

I restarted the manager, modified the file again, and verified that Rule `100002` fired.

## Alert Monitor

I built a monitor around:

```
rule.id = 100002
```

and created the trigger:

```
File Accessed Trigger
```

I validated the monitor by generating another file change and checking the alert history.

## Detection Pipeline

```text
File modification
      |
      v
Wazuh Agent
      |
      v
File Integrity Monitoring
      |
      v
Base integrity event
      |
      v
Custom Rule 100002
      |
      v
Wazuh/OpenSearch Monitor
      |
      v
File Accessed Trigger
```

## What I Learned

This exercise helped me understand that deploying a SIEM is only the beginning. I had to collect telemetry, identify useful events, build a rule, generate test activity, validate the detection, and then investigate the resulting alert.
