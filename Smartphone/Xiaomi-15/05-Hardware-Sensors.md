# Xiaomi 15 Hardware & Sensors

---

## IR Blaster (Mi Remote)

**Hardware:** Top edge. One of the last flagships with IR blaster.

Controls: TV (Samsung, LG, Sony...), AC (Daikin, Mitsubishi...), Set-Top Box, Projector, A/V Receiver.

**Setup:** Open Mi Remote → Add Remote → select category → test power button → save.

---

## NFC

**Position:** Top-rear of phone.

### Uses
| Use | How |
|-----|-----|
| Xiaomi Pay | Settings → Connection & Sharing → NFC → Enable → Wallet app |
| Transit cards | Mi Wallet → Transport Card (varies by region) |
| Tag Read/Write | NFC Tools app (Play Store) |
| HCE Card Emulation | Settings → Connection & Sharing → NFC → Allow HCE |

> ⚠️ NFC **cannot** copy encrypted access cards (MIFARE DESFire). Illegal.

---

## Ultrasonic Fingerprint

**Qualcomm 3D Ultrasonic** — faster, works with wet fingers.

### Tricks
1. Register same finger twice in different angles → improves recognition
2. Assign specific fingerprints to: private space, specific apps, password manager
3. Double-tap gesture via Activity Launcher → open camera, flashlight, screenshot

---

## Accelerometer & Gyroscope

### Calibration
```
Settings → Additional Settings → Accessibility → Motor & Sensors
OR
Dialer → *#*#6484#*#* → Sensor Test → Calibrate
```

**Compass tip:** Figure-8 arm motion recalibrates magnetometer.

### Uses
| Use | How |
|-----|-----|
| Gaming gyro aim | PUBG, Call of Duty — aim by tilting |
| Star Chart | Point at sky → identify constellations |
| Bubble Level | Measure flatness |
| AR apps | Spatial tracking |

> Main game FPS → enable **gyroscope** in game settings. Aim lebih halus + presisi.

---

## Barometer

Measures atmospheric pressure. Uses:
- Altitude (12 hPa per 100m)
- Weather prediction (low = cloudy/rainy)
- Floor detection in tall buildings

**App:** Barometer Plus (Play Store)

---

## GPS

| Feature | Detail |
|---------|--------|
| Constellations | GPS, GLONASS, Galileo, BeiDou, QZSS |
| **Dual-frequency** | **L1 + L5** bands |

**Optimization:** Settings → Location → Locating Method → High accuracy

---

## USB OTG

**Path:** `Settings → Connection & Sharing → OTG → Enable`

Connects: Flash drive, USB mouse, keyboard, game controller, card reader, USB audio interface, Ethernet adapter, external SSD.

**Reverse charging:** Settings → Battery → Reverse charging → Enable (~5W)

---

## Display

### AOD
Runs at ~1Hz on LTPO — minimal battery (~1-2% per 8hr). Dark-themed faces = true zero power on black pixels.

### Reading Mode
Paper-like texture overlay — reduces blue light + unique e-ink feel. Auto-enable based on ambient light.

### Color Schemes
| Mode | Best For |
|------|---------|
| **Original** | Most accurate, DCI-P3 |
| **Saturated** | Vivid colors |
| **AMOLED** | High contrast |
| **Standard** | sRGB, reading |

---

## Haptic Feedback

**X-axis linear vibration motor** — highest quality type.

Tips:
- Gaming haptics: Enable in Genshin/PUBG settings
- Keyboard haptics: Gboard → Preferences → Key press vibration

---

## Speaker & Audio

| Feature | Detail |
|---------|--------|
| Dolby Atmos | Smart / Movie / Music / Game / Voice presets |
| Hi-Res Audio | Wired + wireless (LDAC) |
| Codecs | LDAC, aptX, aptX HD, AAC, SBC |

**LDAC settings:** Settings → Additional Settings → Developer Options → Bluetooth Audio LDAC
- 990kbps = near-lossless
- 660kbps = balanced quality/battery

---

## Sensors Quick Reference

| Sensor | Primary | Hidden Use |
|--------|---------|-----------|
| **IR Blaster** | Remote control | DIY automation |
| **NFC** | Payments | Tag R/W, HCE |
| **Ultrasonic FP** | Unlock | App shortcuts, 2nd space |
| **Accelerometer** | Auto-rotate | Gaming, level, star-gazing |
| **Gyroscope** | Gaming gyro | AR, rotation |
| **Barometer** | Weather | Altitude, floor |
| **GPS** | Navigation | L1+L5 accuracy |
| **Ambient Light** | Auto-brightness | Lux meter |
| **X-axis Motor** | Vibration | Gaming haptics |

---

*Last updated: August 2026 — HyperOS 2 / Android 15*
