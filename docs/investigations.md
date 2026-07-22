# Investigation Notes

This document contains short investigation write-ups from the lab exercises.

---

## Investigation 1: SSH Brute Force Attempt

**Date:** July 21, 2026  
**Agent:** testendpoint (172.16.189.128)  
**Severity:** High (Custom Rule 100100 – Level 12)

### Summary
Multiple failed SSH login attempts were detected against the Ubuntu endpoint. Both valid and non-existent usernames were targeted.

### Key Alerts
- Default rules: 5710, 5503, 5760, 5763, 2502
- Custom rule: **100100** (Multiple failed SSH login attempts - possible brute force)
- MITRE ATT&CK: T1110 – Brute Force

### Timeline
- Multiple authentication failure events occurred within a short time window
- Wazuh correlated the events and triggered the custom high-severity rule

### Outcome
- Activity was generated intentionally for testing
- Custom rule successfully detected and elevated the event
- Demonstrates working rule chaining and MITRE mapping

---

## Investigation 2: File Integrity Monitoring – /etc Changes

**Date:** July 22, 2026  
**Agent:** testendpoint  
**Severity:** Medium-High (Custom Rule 100101 – Level 10)

### Summary
Files were created, modified, and deleted under the `/etc` directory to test File Integrity Monitoring.

### Key Alerts
- Default FIM rules: 553 (File deleted), 554 (File added)
- Custom rule: **100101** (Sensitive file change detected under /etc)
- MITRE ATT&CK: T1565.001 – Stored Data Manipulation

### Outcome
- Syscheck successfully detected the changes after frequency was adjusted for lab use
- Custom rule correctly highlighted activity in a critical directory

---

## Notes for Future Investigations
- Add process creation visibility with auditd
- Expand custom rules for more specific suspicious behaviors
- Include full event JSON and screenshots in future write-ups
