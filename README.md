# HP Color LaserJet Pro M254dw — Configuration Reference

A central repository for storing and tracking configuration settings, network details, driver info, and maintenance notes for the HP Color LaserJet Pro M254dw.

---

## Printer Overview

| Field | Details |
|---|---|
| **Model** | HP Color LaserJet Pro M254dw |
| **Part Number** | T6B60A |
| **Type** | Color Laser |
| **Connectivity** | USB, Ethernet, Wi-Fi, Wi-Fi Direct |
| **Duplex** | Automatic (two-sided printing) |

---

## Repository Contents

```
/
├── README.md                   # This file
├── network/
│   └── network-settings.md     # IP address, Wi-Fi, DNS config
├── drivers/
│   └── drivers.md              # Driver versions and download links
├── print-settings/
│   └── defaults.md             # Default paper, quality, duplex settings
├── maintenance/
│   └── log.md                  # Toner replacements, resets, repairs
└── embedded-web-server/
    └── ews-settings.md         # HP EWS (browser-based admin) notes
```

---

## Network Configuration

Document current network settings in `network/network-settings.md`. Suggested fields:

- **IP Address** (static or DHCP-assigned)
- **Subnet Mask**
- **Default Gateway**
- **DNS Servers**
- **Hostname**
- **Wi-Fi SSID**
- **Wi-Fi Direct Name / Password**
- **802.1X / WPA settings** (if applicable)

> ⚠️ Do not commit passwords or WPA keys in plaintext. Use a secrets manager or environment variables and reference them here instead.

---

## Driver & Firmware

Document in `drivers/drivers.md`:

- Current installed driver version (per OS)
- Firmware version on the device
- Links to HP's official support page: [HP M254dw Support](https://support.hp.com/us-en/product/hp-color-laserjet-pro-m254dw/15096270)
- Notes on any known driver issues or workarounds

---

## Default Print Settings

Document in `print-settings/defaults.md`:

- Paper size (e.g., A4 / Letter)
- Print quality (Draft / Normal / Best)
- Color vs. Grayscale default
- Duplex on/off
- Tray assignments

---

## Embedded Web Server (EWS)

The M254dw has a built-in web interface accessible at the printer's IP address (e.g., `http://192.168.1.x`). Document any custom EWS settings in `embedded-web-server/ews-settings.md`, such as:

- Admin password (store securely — do not commit here)
- Energy save / sleep settings
- Security settings (SNMPv1/v2/v3, SSL)
- Email / scan-to-email configuration

---

## Maintenance Log

Track servicing events in `maintenance/log.md`:

| Date | Event | Notes |
|---|---|---|
| YYYY-MM-DD | Toner replaced (Black) | |
| YYYY-MM-DD | Firmware updated | Version X → Version Y |
| YYYY-MM-DD | Paper jam cleared | Tray 2 |

---

## Useful Links

- [HP M254dw Product Page](https://www.hp.com/us-en/shop/pdp/hp-color-laserjet-pro-m254dw)
- [HP Support & Drivers](https://support.hp.com/us-en/product/hp-color-laserjet-pro-m254dw/15096270)
- [HP EWS Documentation](https://support.hp.com/us-en/document/c04706744)
- [HP Smart App](https://www.hp.com/us-en/shop/cv/hpsmart)

---

## Contributing

To update configuration details:
1. Edit the relevant file in the appropriate subfolder.
2. Add a brief commit message describing what changed (e.g., `Update static IP address`).
3. For major changes (firmware updates, network reconfigs), add an entry to `maintenance/log.md`.

---

## License

This repository contains configuration reference information only. No warranty is implied. HP trademarks and product names belong to HP Inc.
