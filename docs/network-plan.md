# Network plan (MVP)

## Zones
- **MGMT**: management access only (hypervisor / firewall admin)
- **CORP**: AD + endpoints + services
- **SOC**: SIEM and analysis tooling

## Addressing (proposed)
> Final addressing may change; keep it consistent across docs and screenshots.

- MGMT: `10.10.10.0/24` (GW: `10.10.10.1`)
- CORP: `10.20.20.0/24` (GW: `10.20.20.1`)
- SOC:  `10.30.30.0/24` (GW: `10.30.30.1`)

## Assets (MVP)
- **FW01 (OPNsense/pfSense)**: WAN + MGMT + CORP + SOC
- **DC01 (Windows Server)**: CORP
- **WIN10-CL01**: CORP
- **SRV01 (service host)**: CORP
- **SOC01 (Wazuh)**: SOC
- **KALI01 (test box)**: CORP

## Baseline firewall policy (MVP)
- Default deny egress from **CORP → WAN**
- Allow only required outbound traffic (e.g., updates) with logging
- Allow **CORP → SOC** telemetry paths (agents/log shipping)
- Restrict access to MGMT to admin workstation(s) only
