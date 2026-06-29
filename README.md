# ZMK firmware for Kambala

The bootloader and compiled firmware can be downloaded in the [releases section](https://github.com/aroum/zmk-kambala/releases). You can change keymap using [this tool](https://nickcoutsos.github.io/keymap-editor/).

-----

## LED Indication

The keyboard features 4 status LEDs (LED 1 to LED 4) to display battery charge, active Bluetooth profiles, and connection status.

### 🔋 Battery Status

*(Legend: 🟢 = Solid ON, 🟡 = Blinking, 🔵 = Blinks onceб ⚫ = OFF)*

When checking battery status (e.g. at startup or when triggered), the first 3 LEDs indicate the battery level:

* **0% – 15%**: LED 1 blinks 3 times ── 🟡 ⚫ ⚫ ⚫
* **16% – 30%**: LED 1 is solid ON ── 🟢 ⚫ ⚫ ⚫
* **31% – 50%**: LED 1 is solid, LED 2 blinks 3 times ── 🟢 🟡 ⚫ ⚫
* **51% – 70%**: LED 1 & 2 are solid ON ── 🟢 🟢 ⚫ ⚫
* **71% – 90%**: LED 1 & 2 are solid, LED 3 blinks 3 times ── 🟢 🟢 🟡 ⚫
* **91% – 99%**: LED 1, 2, and 3 are solid ON ── 🟢 🟢 🟢 ⚫
* **100% (Fully Charged)**: All 3 LEDs blink once together ── 🔵 🔵 🔵 ⚫(Blinking)

### 📶 BLE Profile Selection

When switching active Bluetooth profiles, the corresponding LED blinks once:

* **Profile 1**: LED 1 blinks ── 🔵 ⚫ ⚫ ⚫
* **Profile 2**: LED 2 blinks ── ⚫ 🔵 ⚫ ⚫
* **Profile 3**: LED 3 blinks ── ⚫ ⚫ 🔵 ⚫

### 🔌 USB Powered Animation

When the USB cable is plugged in, a wave animation runs across all 4 LEDs:

1. LEDs turn ON sequentially: LED 1 ➡️ LED 2 ➡️ LED 3 ➡️ LED 4 (🟢 🟢 🟢 🟢)
2. LEDs turn OFF in reverse order: LED 4 ➡️ LED 3 ➡️ LED 2 ➡️ LED 1 (⚫ ⚫ ⚫ ⚫)

### 🔗 Connection Status

#### Bluetooth Connection Status (Central/Left Half)

If the keyboard is active but disconnected from the host device (trying to connect), the LED corresponding to the active profile stays solid ON, while LED 4 blinks once every 4 seconds:

* **Profile 1 disconnected**: 🟢 ⚫ ⚫ 🟡
* **Profile 2 disconnected**: ⚫ 🟢 ⚫ 🟡
* **Profile 3 disconnected**: ⚫ ⚫ 🟢 🟡

*(Legend: 🟢 = Solid ON, 🟡 = Blinking, ⚫ = OFF)*

#### Peripheral Connection Status (Peripheral/Right Half)

If the split peripheral right half loses connection to the central left half:

* **Split disconnected**: ⚫ ⚫ ⚫ 🟡 (LED 4 blinks once every 4 seconds)
