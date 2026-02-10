# FW01 (OPNsense) — Installation and Base Setup

## VM NIC Layout (virt-manager)
FW01 has 4 virtio NICs:
- **WAN**  → `Virtual network 'default': NAT`
- **MGMT** → bridge `br-mgmt`
- **CORP** → bridge `br-corp`
- **SOC**  → bridge `br-soc`

WAN (NAT):
![FW01 WAN NAT](../assets/screenshots/fw01/030-fw01-virtmanager-wan-nat-default.png)

MGMT / CORP / SOC (bridges):
![FW01 MGMT NIC](../assets/screenshots/fw01/040-fw01-virtmanager-nic2-br-mgmt.png)
![FW01 CORP NIC](../assets/screenshots/fw01/041-fw01-virtmanager-nic3-br-corp.png)
![FW01 SOC NIC](../assets/screenshots/fw01/042-fw01-virtmanager-nic3-br-soc.png)

---

## OPNsense Installation (Evidence)
Boot / live login:
![OPNsense live boot](../assets/screenshots/fw01/050-fw01-opnsense-live-boot-login.png)

Installer start and menu:
![Installer start](../assets/screenshots/fw01/051-fw01-installer-start.png)
![Installer options](../assets/screenshots/fw01/052-fw01-installer-menu-install-options.png)

Target disk selection and confirmation:
![Select target disk](../assets/screenshots/fw01/054-fw01-installer-select-target-disk.png)
![Confirm disk wipe](../assets/screenshots/fw01/055-fw01-installer-confirm-disk-wipe.png)

Final install configuration and reboot:
![Final config](../assets/screenshots/fw01/056-fw01-installer-final-config.png)
![Install complete reboot](../assets/screenshots/fw01/057-fw01-installer-complete-reboot.png)

> After installation, detach the ISO so the VM boots from disk.

---

## Interface Mapping (Console)
Initial console menu:
![Console menu](../assets/screenshots/fw01/058-fw01-console-menu-initial.png)

Interface list with MAC addresses (helps map WAN/MGMT/CORP/SOC correctly):
![MAC mapping](../assets/screenshots/fw01/060-fw01-interface-list-mac-mapping.png)

---

## Final IP Plan (FW01)
Target addressing:
- **MGMT**: `10.10.10.1/24`
- **CORP**: `10.20.20.1/24`
- **SOC**:  `10.30.30.1/24`
- **WAN**: DHCP via libvirt NAT (`192.168.122.x`)

![Final interface/IP summary](../assets/screenshots/fw01/074-fw01-final-interface-ip-summary.png)

---

## MGMT Workstation and WebGUI Access
MGMT workstation static IPv4 example:
- IP: `10.10.10.10/24`
- Gateway: `10.10.10.1`

![MGMT WS IPv4 config](../assets/screenshots/fw01/091-mgmt-ws-ipv4-manual-config.png)

WebGUI login:
![WebGUI login](../assets/screenshots/fw01/092-opnsense-webgui-login.png)

Initial dashboard:
![Dashboard](../assets/screenshots/fw01/096-fw01-dashboard-initial.png)
