# Custom Detections

This document describes the custom detection rules created in this lab.

## Rule 100100 – Multiple Failed SSH Login Attempts

**Purpose:** Detect possible SSH brute-force attacks by correlating multiple authentication failure events.

**Rule ID:** 100100  
**Level:** 12  
**MITRE ATT&CK:** T1110 (Brute Force)

**Logic:**  
This rule triggers when any of the following default rules fire:
- 5760 (sshd authentication failed)
- 5503 (PAM login failed)
- 5710 (attempt to login with non-existent user)
- 5763 (brute force detected)
- 2502 (multiple password failures)

**Why this rule is useful:**
- Raises severity above the default rules
- Provides a clear, analyst-friendly description
- Explicitly maps the activity to MITRE ATT&CK
- Demonstrates rule chaining (building on existing detections)

---

## Rule 100101 – Sensitive File Change in /etc

**Purpose:** Highlight File Integrity Monitoring events that occur in the critical `/etc` directory.

**Rule ID:** 100101  
**Level:** 10  
**MITRE ATT&CK:** T1565.001 (Stored Data Manipulation)

**Logic:**  
Triggers on top of default FIM rules (550, 553, 554) when the affected file path contains `/etc/`.

**Why this rule is useful:**
- Focuses attention on changes to system configuration files
- Increases severity for a high-value directory
- Shows understanding of FIM use cases

---

## Notes

- Custom rules are stored in `/var/ossec/etc/rules/local_rules.xml` on the Wazuh manager.
- Rule IDs 100000+ are reserved for local/custom rules.
