# SOC Portfolio

Hands-on Security Operations Center labs focused on SIEM monitoring, alert triage, log analysis, detection rules, and investigation documentation.

## What This Portfolio Demonstrates

- Elastic Security / SIEM investigation
- Alert triage and disposition
- Process and command-line analysis
- Windows endpoint telemetry
- KQL and ES|QL queries
- Detection rule development and tuning
- False-positive analysis
- Basic incident investigation and documentation
- Security event validation using endpoint telemetry

## Labs

### PowerShell Reconnaissance Detection
A lab using Elastic Security to detect simulated Windows host-discovery activity generated through PowerShell.

The investigation covers:
- Process creation telemetry
- PowerShell Script Block Logging (Event ID 4104)
- KQL and ES|QL queries
- Telemetry validation
- Query refinement and result review

### Process Execution & Discovery Triage
A lab that simulates administrative discovery commands, creates a custom Elastic detection, and walks through the alert-triage process.

The investigation focuses on:
- Process execution and command-line context
- Parent/child process relationships
- Alert validation
- Distinguishing authorized administrative activity from potentially suspicious behavior
- Documenting a false-positive disposition

## SOC Workflow

The labs follow an analyst-oriented workflow:

**Generate telemetry → Detect → Validate → Investigate → Determine severity → Document → Escalate or close**

The goal is to demonstrate practical security operations work rather than claim production SOC ownership.

## Tools & Technologies

- Elastic Security / Elastic SIEM
- Elastic Agent / Elastic Defend
- KQL
- ES|QL
- Windows event telemetry
- PowerShell
- Process and command-line analysis
- MITRE ATT&CK concepts
- Git / GitHub

## Areas for Continued Development

Future labs can expand into endpoint investigation, network telemetry, phishing analysis, threat hunting, cloud security events, and basic automation.

## Portfolio Note

All activity in this repository is performed in a lab or simulated environment for learning and portfolio purposes. The examples do not represent access to or investigation of a real production environment.
