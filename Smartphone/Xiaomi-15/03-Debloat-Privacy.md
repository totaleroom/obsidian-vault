# Xiaomi 15 Debloat & Privacy Guide

---

## 🔴 DO NOT Remove (Bricks Device)

| Package | Why |
|---------|-----|
| `com.miui.securitycenter` | Core security framework |
| `com.miui.finddevice` | Find My Device |
| `com.android.contacts` | Contacts |
| `com.android.updater` | System updater |
| `com.miui.home` | Launcher |
| `com.miui.packageinstaller` | App installer |
| `com.xiaomi.market` | Mi Market |
| `com.xiaomi.account` | Mi Account |

---

## 🔴 High-Priority Disable (Analytics/Ads)

```bash
adb shell pm disable-user --user 0 com.miui.msa.global     # Core ad framework — MOST IMPACTFUL
adb shell pm disable-user --user 0 com.miui.analytics         # Analytics/tracking
adb shell pm disable-user --user 0 com.miui.systemAdSolution  # System ad solution
adb shell pm disable-user --user 0 com.xiaomi.ab              # Analytics
adb shell pm disable-user --user 0 com.google.android.gms.location.history  # Location history
```

---

## MIUI Ads Removal (No PC)

```
Settings → Passwords & Security → Privacy → Ad Services → Toggle OFF "Personalized services"
```

### Per-App Ad Settings
| App | Path to Disable |
|-----|----------------|
| Music | Settings → Advanced → Show ads → OFF |
| Themes | Account → Settings → Personalization → OFF |
| Weather | Settings → Weather info → Ads → OFF |
| GetApps | Account → Settings → Privacy → Personalized → OFF |
| Mi Browser | Settings → Privacy → Personalized search → OFF |

---

## Privacy Settings Checklist

- [ ] Ad Services → Personalization → OFF
- [ ] Location → Google Location Accuracy → OFF
- [ ] Virtual ID → Disable for all apps, reset ID
- [ ] Usage Data & Diagnostics → OFF
- [ ] Analytics → OFF
- [ ] Review all app permissions
- [ ] Hidden Album → fingerprint lock
- [ ] App Lock → Banking, WhatsApp → biometric ON

---

## One-Click Debloat Script

```bash
#!/bin/bash
PACKAGES=(
  "com.miui.analytics"
  "com.miui.systemAdSolution"
  "com.miui.msa.global"
  "com.xiaomi.ab"
  "com.google.android.gms.location.history"
  "com.facebook.katana"
  "com.facebook.appmanager"
  "com.spotify.music"
  "com.netflix.mediaclient"
)
for pkg in "${PACKAGES[@]}"; do
  adb shell pm disable-user --user 0 "$pkg"
done
```

---

## ROM Comparison

| Feature | CN ROM | Global ROM | Xiaomi.eu |
|---------|--------|------------|-----------|
| Google Services | ❌ | ✅ | ✅ |
| Ads | Extensive | Moderate | Minimal |
| Notification Reliability | Poor | Good | Good |
| **Recommendation** | ❌ | ✅ | ✅ **Best** |

---

*Last updated: August 2026 — HyperOS 2*
