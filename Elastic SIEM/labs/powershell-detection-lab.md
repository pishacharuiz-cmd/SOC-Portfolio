# PowerShell Reconnaissance Detection Lab

## Overview

This lab uses Elastic Security to detect simulated Windows host-discovery activity generated through PowerShell. The focus is on validating endpoint telemetry, writing practical SIEM queries, and reviewing the resulting events.

## Objectives

- Generate a known PowerShell discovery event in a lab environment.
- Verify process creation and command-line telemetry.
- Review PowerShell Script Block Logging (Event ID 4104).
- Write equivalent KQL and ES|QL queries.
- Validate that the expected event data is searchable in Elastic.

## Detection Queries

### KQL — Process Creation

```kql
process.name : "powershell.exe" and process.command_line : "*Get-ComputerInfo*"
```

### KQL — Script Block Logging

```kql
event.code : "4104" and powershell.file.script_text : "*Get-ComputerInfo*"
```

### ES|QL

```esql
FROM logs-*
| WHERE process.name == "powershell.exe" AND process.command_line LIKE "*Get-ComputerInfo*"
```

## Investigation & Validation

1. **Generate telemetry:** Execute the discovery command in the monitored lab endpoint.
2. **Review event data:** Confirm the process name, command line, and available PowerShell logging fields.
3. **Run the queries:** Test the detection logic in Elastic Discover.
4. **Validate results:** Confirm that the returned event matches the expected activity.
5. **Review query behavior:** Compare KQL and ES|QL syntax and refine the search when needed.

## Analyst Takeaway

The exercise shows why endpoint logging needs to be configured before a detection can be useful. A rule may be logically correct but still produce no results if the required process or PowerShell telemetry is not being collected.

## Portfolio Note

This activity was performed in a lab environment using simulated discovery behavior. It is intended to demonstrate SIEM query development and investigation workflow, not production incident response.
