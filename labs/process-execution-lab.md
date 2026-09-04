Lab: Detection Engineering & Triage - Process Execution & Discovery

    Objective: Simulate host-based reconnaissance activity, deploy a custom detection rule in Elastic SIEM, analyze telemetry, and execute an end-to-end alert triage workflow.

    Environment: Elastic Security (Elastic Agent / Elastic Defend), Windows Endpoint.

1. Threat Simulation

To generate realistic telemetry for administrative discovery behavior, the following command was executed on the endpoint:
DOS

cmd.exe /c "systeminfo & net localgroup administrators"

    Rationale: This command sequence gathers detailed OS configuration data via systeminfo and queries local group memberships via net, a common discovery pattern used during early-stage reconnaissance or internal enumeration.

2. Detection Engineering

A custom Process Execution Detection rule was built and deployed within Elastic SIEM to capture suspicious command-line execution patterns targeting host discovery and administrative group enumeration.

    Rule Logic: Monitors process creation events (event.category: process and event.action: started) where command-line arguments match administrative discovery binaries and parameters.

    Initial Outcome: Successfully generated 14 alerts under a Low severity threshold upon simulation execution.

3. Alert Triage & Incident Response

The generated alerts were investigated via the Elastic Security timeline and alert dashboard views to differentiate between malicious activity and authorized administrative tasks.

    Investigation Findings:

        The parent-child process lineage and execution context confirmed the commands were run interactively by an authorized administrator.

        No persistence mechanisms, credential dumping utilities, or lateral movement artifacts were observed in connection with the process execution.

    Triage Action Taken:

        Updated alert status to Closed.

        Classified outcome as False Positive due to authorized administrative user context.

        Documented resolution rationale to complete the incident lifecycle.

4. Evidence & Artifacts

    Active Alerts Dashboard: Showing rule triggers and low severity events.

    Alert Flyout Details: Triage status updated to Closed / False Positive.
