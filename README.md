# Azure VM Diagnostics & Log Analytics

Documentation and screenshots for monitoring Azure virtual machines with diagnostic settings, Windows Event Viewer, and Log Analytics.

## What This Covers

### Diagnostic Settings
- Enabled VM guest diagnostics for application, security, and system logs
- Verified audit failures, application errors, and critical system events are routed to the workspace

### Windows Security Events
- Reviewed Event ID **4625** (failed logon attempts) in the Security log
- Traced sign-in failures and connection timestamps on the host

### Test Event Generation
- Used `eventcreate` from the command line to inject sample events
- Confirmed custom events (Source: `LabTest`, Event ID 100) appear in the pipeline

### Log Analytics & KQL
- Queried the Log Analytics workspace with Kusto (KQL)
- Filtered ingested events by source and event ID:

```kusto
Event
| where Source == "LabTest"
| where EventID == 100
| order by TimeGenerated desc
```

## Repository Contents

Screenshots walk through portal configuration, Event Viewer, synthetic event creation, and query results in Log Analytics.
