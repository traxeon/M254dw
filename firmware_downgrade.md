# Using Cheap Toner on the HP M254dw

HP locked out third-party toner cartridges with a firmware update in October 2020, calling it "Dynamic Security." Firmware **20200612** (June 2020) is the last version before that lockout. This guide walks you through installing it on macOS or Linux.

OEM toner for this printer runs ~$400 a set. Third-party toner is ~$50 for the same set.

---

## Linux: Install Required Software

The commands in this guide use CUPS, which is pre-installed on macOS but needs to be installed on Linux. Install it with your package manager:

**Debian / Ubuntu**
```bash
sudo apt install cups
```

**Fedora / RHEL**
```bash
sudo dnf install cups
```

**Arch**
```bash
sudo pacman -S cups
```

After installing, make sure the printer is added to your system before continuing.

---

## Step 1 - Download the Firmware

HP removed old firmware from their servers, but the Internet Archive has it:

[Download HP_Color_LaserJet_Pro_M254_dw_20200612.rfu](https://web.archive.org/web/20201110192924/http://ftp.hp.com/pub/networking/software/pfirmware/HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu)

The file is ~33.6 MB. After downloading, verify it hasn't been corrupted:

```bash
[ "$(shasum -a 256 HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu | awk '{print $1}')" = "91c7f51ceba2386f3b94dcb9da20c669ab10b1ee3a9b1e1f742c40091920188e" ] && echo "Hash verified" || echo "Hash mismatch - re-download"
```

Don't proceed if you see the mismatch message.

---

## Step 2 - Allow Firmware Changes on the Printer

On the printer's control panel:

Setup > Service > LaserJet Update > Manage Updates

| Setting | Value |
|---|---|
| Allow Downgrade (if downgrading) | Yes |
| Allow Updates (if upgrading) | Yes |
| Prompt Before Install | Install Automatically |

Without this, the printer will reject the file.

---

## Step 3 - Find Your Printer Name

Open a terminal and run:

```bash
lpstat -p -d
```

You'll see something like:

```
printer HP_Color_LaserJet_M254DW_0 is idle.
```

Note that name, you'll need it in the next step.

---

## Step 4 - Send the Firmware

Navigate to where you saved the file, then run:

```bash
lpr -P HP_Color_LaserJet_M254DW_0 ./HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu
```

Replace `HP_Color_LaserJet_M254DW_0` with your actual printer name.

The printer will receive the file and start updating automatically. Don't turn it off. The whole process takes 5-10 minutes, including a progress bar and a reboot.

---

## Step 5 - Verify

Once the printer comes back up, print a configuration page from the control panel and confirm the firmware version shows `20200612`.

---

## Step 6 - Disable Automatic Updates

If you skip this, HP will push the DRM firmware back onto your printer automatically.

Setup > Service > LaserJet Update > Manage Updates

| Setting | Value |
|---|---|
| Allow Updates | No |
| Check Automatically | Off |
| Prompt Before Install | Always Prompt |

---

## Quick Reference

```bash
# Linux only: install CUPS
# Debian/Ubuntu: sudo apt install cups
# Fedora/RHEL:   sudo dnf install cups
# Arch:          sudo pacman -S cups

# 1. Download firmware from Internet Archive (see link above)

# 2. Verify hash
[ "$(shasum -a 256 HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu | awk '{print $1}')" = "91c7f51ceba2386f3b94dcb9da20c669ab10b1ee3a9b1e1f742c40091920188e" ] && echo "Hash verified" || echo "Hash mismatch - re-download"

# 3. On the printer: Setup > Service > LaserJet Update > Manage Updates > Allow Downgrade: Yes

# 4. Find your printer name
lpstat -p -d

# 5. Send firmware
lpr -P HP_Color_LaserJet_M254DW_0 HP_Color_LaserJet_Pro_M254_dw_Printer_series_20200612.rfu

# 6. Wait 5-10 min, then disable auto-updates on the printer
```

---

## Notes

- The M254dw doesn't have anti-rollback protection, so you can go up or down in firmware version freely.
- If you ever factory reset the printer, re-disable automatic updates as a reset may turn them back on.
- Third-party toner quality is effectively identical to OEM for everyday printing.

