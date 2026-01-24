# ISO inventory (local-only)

All ISO images are stored locally and are **NOT committed** to this repository.

## Local path
- `~/soc-lab/isos/`

## Verification
After downloading each ISO, record its SHA256:

```bash
cd ~/soc-lab/isos
sha256sum <file>.iso

Inventory
Component	ISO file (local)	Version	SHA256	Source	Download date
FW01	OPNsense-25.7-dvd-amd64.iso	25.7	36ec856ad34d1a497e9edd19183ac2b63aa3f9bb9ff7e7ff7cdc93d319a3ec2c	Official OPNsense download page	2026-01-24
DC01	SERVER_EVAL_*.iso	Windows Server 2022 Eval	<fill>	Microsoft Evaluation Center	YYYY-MM-DD
WIN client	Win11_*.iso	<fill>	<fill>	Microsoft Software Download	YYYY-MM-DD
SOC01	ubuntu-*-live-server-amd64.iso	Ubuntu Server LTS	<fill>	Ubuntu Server download page	YYYY-MM-DD
KALI01	kali-linux-*.iso	<fill>	<fill>	Official Kali images	YYYY-MM-DD
