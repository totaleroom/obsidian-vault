# Xiaomi 15 Advanced Configurations

---

## Essential Dialer Codes

| Code | Function |
|------|----------|
| `*#*#4636#*#*` | Phone Information — battery, network, call stats |
| `*#*#6485#*#*` | **Battery info** — cycle count (MF_02), health (MF_05), voltage, temp |
| `*#06#` | IMEI number |
| `*#*#2663#*#*` | Touchscreen firmware version |
| `*#*#0283#*#*` | Audio loopback / speaker test |
| `##3646633##` | **MTK Engineer Mode — NOT for Snapdragon 8 Elite (Xiaomi 15 uses Qualcomm)** |

---

## ADB Setup

1. Enable Developer Options → 7x tap MIUI/HyperOS version
2. `Settings → Additional Settings → Developer Options → USB debugging → ON`
3. On PC: `adb devices` to verify

### Essential Commands

```bash
# Reboot
adb reboot              # Normal
adb reboot recovery     # Recovery
adb reboot fastboot    # Fastboot

# Disable bloatware
adb shell pm disable-user --user 0 com.miui.msa.global     # MOST IMPACTFUL
adb shell pm disable-user --user 0 com.miui.analytics
adb shell pm disable-user --user 0 com.miui.systemAdSolution

# Info
adb shell dumpsys battery          # Battery stats
adb shell pm list packages         # All packages
adb shell getprop | grep "ro.build"  # Build info

# Screen
adb shell screencap /sdcard/screenshot.png
adb shell screenrecord /sdcard/screen.mp4
```

---

## Display Calibration

| Mode | Description |
|------|-------------|
| **Original** | DCI-P3 wide gamut, most accurate (default) |
| **Saturated** | Vivid, boosted colors |
| **AMOLED** | High contrast |
| **Standard** | sRGB, neutral — reading |

Path: `Settings → Display → Color scheme` + `Color temperature`

---

## Audio — Dolby Atmos

**Path:** `Settings → Sound & Vibration → Dolby Atmos`

| Preset | Best For |
|--------|---------|
| Smart | AI-selected per content |
| Movie | Cinematic, dialogue clarity |
| Music | Balanced |
| Game | Enhanced positional, bass |
| Voice | Podcast, audiobook |

**Custom EQ:** 6-band (60Hz, 230Hz, 910Hz, 3.6kHz, 7.2kHz, 14kHz)

For clarity: boost 3–6kHz slightly, cut 60–100Hz if muddy.

---

## Battery Cycle Count

```
*#*#6485#*#*
```
Shows: MF_02 (cycle count), MF_05 (health %), MF_06 (voltage), MF_07 (temp), MF_08 (remaining capacity)

**Apps:** AccuBattery (Play Store) — tracks cycles + capacity loss over time

---

## Camera RAW / DNG

1. Camera → **PRO** (Manual) mode
2. Look for **RAW** or **DNG** toggle
3. DNG files → `/DCIM/Camera/` → process with Lightroom Mobile or Snapseed

---

## ROM Comparison

| Feature | CN ROM | Global ROM | Xiaomi.eu |
|---------|--------|------------|-----------|
| Google | ❌ | ✅ | ✅ |
| Ads | Extensive | Moderate | Minimal |
| Updates | Fastest | Slower | Fast (weekly) |
| **Rec** | ❌ | ✅ | ✅ **Best** |

**xiaomi.eu:** https://xiaomi.eu/community/

---

## Bootloader Unlock

**⚠️ Warning:** Requires Xiaomi account + 72-hour wait. Wipes all data. Anti-rollback protection = brick risk if downgrade.

### Steps
1. Install **Xiaomi Community** app
2. Sign in with Xiaomi Account
3. Go to **Me → Unlock Bootloader** → wait 72 hours
4. Download **Mi Unlock Tool** from https://en.miui.com/unlock/
5. Backup everything
6. Boot to **Fastboot** (Power + Volume Down)
7. Run Mi Unlock Tool → click Unlock

---

## Custom ROM Status (2026)

| ROM | Status |
|-----|--------|
| LineageOS 23.2 (Android 16) | Unofficial |
| LineageOS 22.2 (Android 15) | Unofficial |
| **Official LineageOS** | Not yet released |
| **xiaomi.eu HyperOS** | Active weekly builds |
| Evolution X | Some Xiaomi 14/15 support |

**Magisk (Root without ROM):** Flash Magisk patched boot image via Fastboot. Enables systemless hide, Xposed/Zygisk modules, ad blocking.

---

## Quick Reference

```
Daily Codes:
  *#*#6485#*#*  → Battery cycle count + health
  *#*#4636#*#*  → Phone info + network
  *#06#          → IMEI

Safe Disable (High Priority):
  com.miui.msa.global        ← MOST IMPACTFUL (ads)
  com.miui.analytics
  com.miui.systemAdSolution
  com.xiaomi.ab
```

---

*Last updated: August 2026 — HyperOS 2 / Android 15*
