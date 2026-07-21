<<<<<<< HEAD
# Endpoint Detection Lab – Wazuh SIEM

A professional-grade personal SIEM / endpoint detection laboratory built to demonstrate detection engineering, compliance monitoring, and incident response skills.

**Purpose**: Showcase hands-on security operations capabilities relevant to Endpoint Security Engineer, Detection Engineer, and SOC Analyst roles.

## Architecture Overview
- **SIEM Platform**: Wazuh (single-node deployment via Docker)
- **Host**: macOS (Intel) with resource-constrained Docker Desktop
- **Monitored Endpoints**: Ubuntu Server 24.04 VM (primary agent) + optional lightweight container agent
- **Key Capabilities Demonstrated**:
  - Agent-based endpoint telemetry
  - File Integrity Monitoring (FIM)
  - Custom detection rules with MITRE ATT&CK mapping
  - Alert investigation and documentation
  - Security hygiene and least-privilege design

*(Architecture diagram to be added in `/architecture/`)*

## Skills Demonstrated
- SIEM deployment and operations
- Detection rule authoring and tuning
- Log analysis and incident response
- Compliance-focused monitoring (SOC 2 aligned)
- Secure lab design and documentation

## Quick Start
```bash
# Start the lab
docker compose up -d

# Stop the lab
docker compose down
