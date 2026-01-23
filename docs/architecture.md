# Architecture (MVP)

## Goal
Build a corporate-style lab with AD and a minimal SOC workflow:
**detect → triage → respond → close**.

## Components
- **Identity**: DC01 (AD DS + DNS)
- **Endpoints**: WIN10-CL01 (Sysmon + SIEM agent)
- **Services**: SRV01 (test services)
- **SOC**: SOC01 (Wazuh SIEM + dashboards)
- **Network control**: FW01 (segmentation + containment)

## Data flow (high level)
1. Endpoints/servers generate logs (Windows events, Sysmon, service logs)
2. SIEM ingests logs and generates alerts
3. Analyst triages alert and collects evidence
4. Response actions applied (firewall block / hardening)
5. Incident is closed (TP/FP) and detections are tuned

## MVP scenarios
- 001 Recon / Port scan
- 002 RDP brute force
