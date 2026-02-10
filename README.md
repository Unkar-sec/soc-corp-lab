# SOC Corporate Lab — AD + Wazuh SIEM + Incident Response (Portfolio)

This repository documents building a realistic “corporate-style” security lab from scratch and running SOC workflows on top of it:
- **Active Directory** (Windows Server) + domain-joined endpoints
- centralized logging and detections (**Wazuh SIEM**)
- incident handling: **triage → response → closure** (TP/FP)
- network segmentation + containment (firewall policies)

The goal is a recruiter-friendly portfolio: architecture, configs, detections, runbooks, and incident write-ups with evidence.

## Recruiter highlights (what this demonstrates)
- KVM/libvirt networking: NAT + Linux bridges (segmentation)
- OPNsense multi-NIC firewall design + interface mapping
- Least privilege policy: whitelist + BLOCK+LOG (with evidence)
- Admin hardening: WebGUI restricted to MGMT only
  
---

## Project goals
- Build a realistic baseline enterprise environment (AD, endpoints, services, segmentation).
- Collect host + network telemetry and generate actionable alerts.
- Practice SOC incident response with proper documentation: **evidence → timeline → decisions → actions → lessons learned**.
- Keep everything reproducible and clearly documented.

---

## Lab safety model
All testing is done in an isolated lab environment:
- Segmented networks: **MGMT / CORP / SOC** (+ optional MAL later).
- Policy: **only the firewall (FW01) has controlled WAN access**; other VMs do not directly touch the home network.
- No host↔guest convenience channels for risky VMs: shared folders / clipboard / drag&drop = **OFF**.
- Use disposable VMs: snapshot → test → revert.
- Focus on **TTP simulations and safe test scenarios** (no destructive payloads).

---

## Stack (MVP)
**Virtualization (host):**
- Linux host + **KVM/libvirt** (virt-manager).  
  *(Hypervisor-agnostic: architecture + documentation matter most.)*

**Network:**
- **FW01 (OPNsense/pfSense)** — routing, ACLs, traffic logging
- Segmentation: **MGMT / CORP / SOC**

**Endpoints / servers:**
- **DC01 (Windows Server)** — AD DS + DNS
- **WIN10-CL01** — domain-joined endpoint + Sysmon
- **SRV01** — test service host (web / file share / small app)

**SOC:**
- **SOC01 (Wazuh)** — agents, dashboards, rules, alerts
- (Phase 2) TheHive / Suricata or Zeek — case management / NIDS

---

## MVP scope
- [ ] Network plan and addressing (MGMT/CORP/SOC)
- [ ] FW01 with **deny-by-default egress** policy
- [ ] DC01: domain bootstrap + DNS
- [ ] WIN10-CL01: join domain + Sysmon
- [ ] SOC01: Wazuh + dashboards + agents
- [ ] Scenarios + write-ups:
  - **001 Recon / Port scan** (detection + containment + TP)
  - **002 RDP brute force** (detection + containment + hardening)

---

## Repository layout
soc-corp-lab/
docs/
architecture.md
network-plan.md
threat-model.md
runbooks/
triage-portscan.md
triage-rdp-bruteforce.md
assets/
diagrams/
screenshots/
infrastructure/
firewall/
ad/
endpoints/
soc/
detections/
wazuh/
incidents/
_TEMPLATE/
001-portscan/
002-rdp-bruteforce/
scripts/


---

## Incident write-up standard
Each incident in `incidents/<ID>/` includes:
- Executive summary
- Scope (assets, zone, accounts)
- Detection details (data sources, rule/alert)
- Timeline
- Triage (hypotheses, correlation, TP/FP decision)
- Response (containment / eradication / recovery)
- Detection tuning (reduce false positives)
- Lessons learned

Template: `incidents/_TEMPLATE/INCIDENT.md`

> Note: raw artifacts (pcap/evtx/large logs) are not committed to a public repo.
> Only screenshots, sanitized snippets, and (optionally) hashes are included.

---

## Roadmap (Phase 2)
- [ ] NIDS (Suricata or Zeek) + SIEM correlation
- [ ] Case management (TheHive)
- [ ] Additional scenarios: suspicious PowerShell/LOLBins, lateral movement, phishing/URL
- [ ] Hardening: GPO baselines, account lockout policies, service segmentation

---

## How to use this repo
- Start here: `docs/network-plan.md` and `docs/architecture.md`
- Setup/config: `infrastructure/`
- Detections: `detections/wazuh/`
- Incident reports: `incidents/`

### Networking & Firewall (FW01)
- [Host networking (KVM/libvirt)](docs/host-networking-kvm.md)
- [FW01 OPNsense setup](docs/fw01-opnsense-setup.md)
- [FW01 firewall policy (MGMT/CORP/SOC)](docs/fw01-firewall-policy.md)

---

## License
MIT License.
