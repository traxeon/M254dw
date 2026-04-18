# HP Color LaserJet Pro M254dw — Firmware & Cheap Toner Guide

This repository exists to preserve a known-good **pre-DRM firmware** for the **HP Color LaserJet Pro M254dw** and document how to install it so the printer continues to accept **third-party toner**.

HP introduced a "Dynamic Security" lockout for non-HP cartridges via a firmware update around **October 2020**. Firmware **20200612** (June 2020) is the last version prior to that lockout (see `firmware_downgrade.md`).

## What’s in this repo

- `HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu` — the firmware image (~33.6 MB)
- `HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu.sha256` — checksum for integrity verification
- `firmware_downgrade.md` — step-by-step downgrade/install instructions (Linux/CUPS + `lpr`)

## Quick start

1. Verify the firmware file:

   ```bash
   shasum -a 256 HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu
   ```

   Compare against the value in `HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu.sha256`.

2. Follow the full install/downgrade guide:

   - See `firmware_downgrade.md`

3. After the downgrade, **disable automatic updates** on the printer to prevent HP from re-installing the newer firmware.

## Safety / responsibility

Firmware flashing always carries risk (power loss, wrong model, etc.). Use at your own risk. This repo is provided for documentation and archival purposes.

## License / trademarks

No warranty is implied. HP trademarks and product names belong to HP Inc.
