# Wazuh SIEM Lab — Findings Report

## Executive Summary
This lab deployed Wazuh SIEM to simulate and detect three 
common attack patterns seen in real SOC environments. 
Three custom detection rules were written, tested, and 
mapped to MITRE ATT&CK techniques.

## Attacks Simulated

### 1. SSH Brute Force
**Tool used:** Hydra / manual failed logins
**Result:** Rule 100001 fired after 5 failed attempts 
within 60 seconds
**Alert level:** 10 (High)
**Detection time:** Under 60 seconds from attack start

### 2. Reverse Shell
**Tool used:** Netcat / Metasploit handler
**Result:** Rule 100002 fired on detection of bash 
spawned by non-shell parent
**Alert level:** 12 (Critical)
**Detection time:** Immediate on process creation

### 3. Privilege Escalation
**Tool used:** Manual sudo failure simulation
**Result:** Rule 100003 fired after 3 sudo failures 
in 120 seconds
**Alert level:** 10 (High)
**Detection time:** Under 2 minutes

## Triage Findings
All three alerts were classified as True Positives in 
the lab environment. Each was investigated using the 
5-step triage workflow documented in the main README.

## Rule Tuning Notes
- Brute force threshold set at 5 attempts to balance 
  sensitivity vs false positives from legitimate 
  failed logins
- Reverse shell rule requires further tuning to exclude 
  legitimate scripted processes in production environments
- Privilege escalation rule most effective when combined 
  with user behavior baseline

## Conclusion
SIEM deployment confirmed functional. Detection rules 
operational. Lab demonstrates core Tier 1 SOC workflow: 
receive alert → investigate → classify → escalate or close.
