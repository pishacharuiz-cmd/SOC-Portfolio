# Lab Report: Detecting PowerShell Reconnaissance with Elastic SIEM

## Overview
This lab focuses on detection engineering and log analysis within Elastic Security. The objective was to simulate and detect local reconnaissance activity—specifically, host discovery via PowerShell execution (`Get-ComputerInfo`)—using both Kusto Query Language (KQL) and ES|QL.

---

## Lab Objectives
* Simulate a common host discovery technique using PowerShell (`Get-ComputerInfo`).
* Verify process creation and command-line logging via Elastic Agent telemetry.
* Develop and execute detection queries in both **KQL** and **ES|QL** to filter security logs.

---

## Detection Engineering & Queries

### 1. KQL Process Creation Query
To identify instances where `powershell.exe` was invoked with arguments related to system discovery:

```kql
process.name : "powershell.exe" and process.command_line : "*Get-ComputerInfo*"
2. KQL Script Block Logging Query (Event ID 4104)

To capture script block content containing the discovery command:
Code snippet

event.code : "4104" and powershell.file.script_text : "*Get-ComputerInfo*"

3. ES|QL Detection Query

For environments utilizing ES|QL for advanced tabular data processing and threat hunting:
Code snippet

from logs-* 
| where process.name == "powershell.exe" and process.command_line like "*Get-ComputerInfo*"

Investigation Steps & Validation

    Step 1 — Telemetry Generation: Executed a monitored PowerShell process invocation forcing command-line parameter logging (Get-ComputerInfo).

    Step 2 — Index / Query Tuning: Verified that the query language setting in Discover matched the syntax being used (switching correctly between KQL and ES|QL modes).

    Step 3 — Result Validation: Confirmed event capture via Elastic Agent and successfully isolated the process execution parameters in the SIEM dashboard.

Conclusion

This lab demonstrates the necessity of proper endpoint telemetry configuration (such as process creation auditing and command-line logging) and highlights the syntax differences when querying security logs across KQL and ES|QL engines.
