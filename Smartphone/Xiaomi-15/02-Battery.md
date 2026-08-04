# Xiaomi 15 Battery Optimization

---

## Key Settings Path
`Settings → Battery & Performance`

---

## Power Modes

| Mode | CPU/GPU | Best For |
|------|---------|----------|
| **Performance** | Full boost | Gaming |
| **Balanced** | Moderate | Daily (default) |
| **Battery Saver** | Limited | All-day moderate use |
| **Ultra Battery Saver** | Minimal, 5-8 apps | Emergencies, overnight |

---

## 80% Charge Limit (Battery Health)

**Path:** `Settings → Battery → Battery Health & Charging → Charging Limit → 80%`

Stops at 80% to reduce lithium-ion stress. Ideal for overnight charging.

---

## LTPO & Refresh Rate

Xiaomi 15 has **LTPO OLED** — drops to 1Hz when static.

| Mode | Feel | Battery vs 60Hz |
|------|------|----------------|
| **Auto** (LTPO) | Smooth + drops to 1Hz idle | ~8-12% more drain |
| **120Hz Forced** | Same when moving | ~12-15% more drain |
| 60Hz | Standard | Baseline |

**→ Keep "Auto"** — most efficient.

---

## Overnight Setup

1. **Ultra Battery Saver** — allows only alarm + essentials
2. **Sleep Standby Optimization** — freezes background during detected sleep
3. **Overnight Hibernation** — deep-suspends apps + network radios
4. **AOD off** or scheduled

---

## Background App Management (5 Layers)

**Layer 1:** `Settings → Battery → App Battery Saver → [App] → No Restrictions`
**Layer 2:** `Settings → Apps → Autostart → ON`
**Layer 3:** Open recent apps → drag app **down** to lock (padlock icon)
**Layer 4:** `Settings → Battery → Battery optimization → [App] → Don't optimize`

---

## Quick Battery Checklist

- [ ] 80% charge limit ON
- [ ] Refresh rate: Auto
- [ ] Dark mode ON (OLED power savings)
- [ ] 5G → switch to LTE if signal weak
- [ ] Bluetooth OFF if not used
- [ ] Wi-Fi/Bluetooth scanning OFF
- [ ] Sleep Standby Optimization ON
- [ ] Overnight Hibernation ON
- [ ] Unused bloatware disabled

---

## Battery Specs

| Spec | Value |
|------|-------|
| Capacity | 5240 mAh (global) / 5400 mAh (CN) |
| Wired | 90W HyperCharge (~45 min 0→100%) |
| Wireless | 50W HyperCharge |
| SoC | Snapdragon 8 Elite (3nm) |
| PCMark Battery | 13h 44m |

---

*Last updated: August 2026 — HyperOS 2 / Android 15*
