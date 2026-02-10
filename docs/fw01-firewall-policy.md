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
Typical minimal outbound policy for CORP:
- DNS (to defined DNS servers)
- NTP (to defined NTP servers)
- HTTP/HTTPS outbound as required
- Everything else: **BLOCK+LOG**

![CORP rules final](../assets/screenshots/fw01/116-fw01-corp-rules-final.png)

Evidence of blocks in live view/logs:
![CORP live view blocks](../assets/screenshots/fw01/117-fw01-corp-liveview-blocks.png)

---

## SOC Rules — Whitelist + BLOCK+LOG
SOC zone follows the same principle (tight egress + logging). Example policy is shown below.

![SOC rules pending apply](../assets/screenshots/fw01/123-fw01-soc-rules-final-pending-apply.png)
