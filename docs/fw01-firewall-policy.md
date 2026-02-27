# FW01 — Firewall Policy (MGMT / CORP / SOC)

## Goal
Demonstrate basic segmentation and **least privilege**:
- **MGMT**: administrative access (WebGUI) only from MGMT workstation
- **CORP/SOC**: allow only essential outbound services; everything else **BLOCK+LOG**

---

## Interface Naming (Clarity)
Interfaces are labeled with friendly names for readability and long-term maintenance.

![Friendly interface names](../assets/screenshots/fw01/097-fw01-interfaces-friendly-names.png)

---

## Hardening: WebGUI Listens on MGMT Only
The WebGUI is restricted to the MGMT interface to reduce the exposed management surface.

![WebGUI MGMT only](../assets/screenshots/fw01/098-fw01-webgui-listen-mgmt-only.png)

---

## MGMT Rules
Example of tightening defaults and allowing only the required admin traffic (e.g., MGMT-WS → FW01 WebGUI/443).

![MGMT rules](../assets/screenshots/fw01/101-fw01-mgmt-default-allow-disabled.png)

---

## CORP Rules — Whitelist + BLOCK+LOG
CORP uses a minimal egress policy (least privilege):
- DNS via **FW01** (`This Firewall`, TCP/UDP 53)
- NTP to defined NTP servers
- HTTP/HTTPS outbound as required
- Everything else: **BLOCK+LOG**

> CORP clients use `10.20.20.1` (FW01) as their DNS resolver.

![CORP rules (final: DNS via FW01)](../assets/screenshots/fw01/118-fw01-corp-rules-final-dns-via-fw01.png)

Evidence of blocked traffic in Live View:
![Live View: CORP blocked traffic (ICMP)](../assets/screenshots/fw01/119-fw01-liveview-corp-block-icmp.png)

> ICMP is intentionally blocked to demonstrate `BLOCK+LOG` (HTTP/HTTPS still works).

---

## SOC Rules — Whitelist + BLOCK+LOG
SOC zone follows the same principle (tight egress + logging). Example policy is shown below.

![SOC rules pending apply](../assets/screenshots/fw01/123-fw01-soc-rules-final-pending-apply.png)
