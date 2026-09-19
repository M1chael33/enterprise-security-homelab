# Detection Engineering

## Custom Sensitive-File Detection

I created a custom Wazuh rule to make changes to the lab's simulated sensitive file easier to identify.

The XML is stored in:

- [rule-100002.xml](rule-100002.xml)

## Validation Process

I validated the detection by:

1. confirming the Wazuh agent was active,
2. confirming FIM watched the target directory,
3. modifying `secrets.txt`,
4. searching for the generated event,
5. verifying Rule `100002` fired,
6. checking the alert monitor history.

## Detection Workflow

```
Known test action -> endpoint event -> Wazuh rule -> alert monitor -> investigation
```

This gave me a repeatable way to test a detection rather than assuming it worked just because the rule loaded successfully.
