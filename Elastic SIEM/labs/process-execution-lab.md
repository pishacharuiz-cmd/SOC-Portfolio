# Process Execution & Discovery — Detection and Triage Lab

## Objective

Simulate Windows host-discovery activity, create a custom detection rule in Elastic Security, review the generated alerts, and document the triage decision.

## Environment

- Elastic Security / Elastic SIEM
- Elastic Agent / Elastic Defend
- Windows endpoint

## 1. Activity Simulation

The following command sequence was executed in the lab to generate process telemetry:

```cmd
cmd.exe /c "systeminfo & net localgroup administrators"
```

The commands collect operating-system information and local administrator group membership. This type of discovery activity can be legitimate administrative work, but it can also appear during reconnaissance, so context is important during triage.

## 2. Detection Rule

A custom process-execution rule was created to identify command lines associated with host discovery and administrative group enumeration.

The rule uses process creation telemetry and command-line fields to identify matching activity.

**Lab result:** 14 low-severity alerts were generated during the simulation.

## 3. Alert Triage

The alerts were reviewed in the Elastic Security timeline and alert views.

### Investigation checks

- Reviewed process and parent-process context.
- Confirmed the activity was associated with an authorized administrator in the lab.
- Checked for related persistence, credential-access, or lateral-movement indicators.
- Reviewed whether additional suspicious activity was present around the same execution time.

### Disposition

The available lab evidence supported closing the alerts as **false positives / authorized administrative activity**.

The resolution was documented with the reason for closure rather than treating the detection match alone as proof of malicious activity.

## 4. Analyst Takeaways

This lab demonstrates a basic SOC workflow: generate telemetry, create detection logic, validate the alert, investigate surrounding context, and document the final disposition.

It also highlights an important triage consideration: discovery commands should be evaluated in context because the same behavior can be normal for an administrator or suspicious when combined with other indicators.

## Evidence

- Elastic alert results
- Alert details and triage status
- Process execution telemetry
- Investigation notes

## Portfolio Note

This is a simulated lab exercise. The commands and alerts were generated for portfolio purposes and do not represent investigation of a real production environment.
