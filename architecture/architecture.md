# Lab Architecture

## Overview

This lab demonstrates a practical, resource-constrained SIEM deployment using open-source tools. It is designed to be realistic while remaining lightweight enough to run on an 8 GB RAM macOS host.

## Components

### SIEM Stack (Docker)
- **Wazuh Manager** – Receives agent data, analyzes events, and runs detection rules
- **Wazuh Indexer** – Stores and indexes security events (OpenSearch-based)
- **Wazuh Dashboard** – Web interface for visualization, alerting, and investigation

All three components run as Docker containers using the official Wazuh single-node Docker Compose deployment.

### Monitored Endpoint
- **Ubuntu 24.04 Server** running in VMware Fusion
- Wazuh Agent installed and enrolled
- Agent name: `testendpoint`
- Agent IP: `172.16.189.128` (VMware NAT network)

### Host Environment
- macOS (Intel) with 8 GB RAM
- Docker Desktop limited to 4.5 GB RAM and 2 CPUs
- VMware Fusion used for the Ubuntu virtual machine

## Networking

- VMware Fusion networking mode: NAT
- Host (Mac) IP on the VMware network: `172.16.189.1`
- Agent communicates with the Wazuh Manager using the host IP on port 1514
- Dashboard accessible at `https://localhost:443`

## Key Design Decisions

- Single-node Wazuh deployment for simplicity and low resource usage
- Resource limits applied to Docker to keep the host usable
- Syscheck frequency temporarily reduced for faster lab feedback
- Custom rules stored in `local_rules.xml` (IDs 100000+)
- Focus on detection engineering rather than production hardening

## Current Limitations

- Only one agent currently enrolled
- Limited process execution visibility (no auditd yet)
- Self-signed certificates (lab only)
- Not intended for production use
