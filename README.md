# Marlin Configuration - Ender 3 Neo (V4.2.2 - STM32F103RE - TMC2208_STANDALONE)

Customized Marlin firmware configuration for the Creality Ender 3 Neo equipped with the V4.2.2 mainboard.

## Current target: Marlin-bugfix-2.1.x

## Hardware Environment
* **Printer:** Creality Ender 3 Neo
* **Board:** Creality V4.2.2 (STM32F103RE / RC)
* **Drivers:** TMC2208 (Standalone)
* **Build Environment:** `STM32F103RE_creality` using `PlatformIO Core`

## Applied Modifications

### Environment & Safety
* Disabled `NO_CREALITY_422_MCU_WARNING` and `NO_CREALITY_422_DRIVER_WARNING` to bypass compilation alerts regarding hardware validation.

### Geometry
* **Bed Size:** Defined as 220mm x 220mm for X and Y axes. Original example is 235mm x 235mm which is over the limits.

### Motion Control
* **S-Curve Acceleration:** Enabled to provide smoother velocity transitions, reducing mechanical vibration and ringing.

### LCD & Menus
* **PID Tuning Menu:** Enabled `PID_EDIT_MENU` to allow real-time thermal calibration for the Hotend and Heated Bed directly from the printer interface.
* **Individual Axis Homing:** Enabled independent homing menu for X, Y, and Z axes.
* **Status Scrolling:** Enabled `STATUS_MESSAGE_SCROLLING` to allow long filenames and system messages to scroll across the LCD.

## Post-Flash Procedure
1.  **Initilaize EEPROM:** go to "configuration", go to "Advanced Settings" and then press "Initilaize EEPROM".
2.  **Probe Z Offset:** enter your Z-Offset or set a new one.
3.  **K-Factor Calibration:** Use `M900 K0.6` as a baseline. Perform a line test to find the optimal K-value for specific filament brands/types. Override with `M900 K<mm>` during start G-Code.
4.  **Autotune PID:** Go to "configuration" -> "temperature" -> PID AutoTune.
3.  **Save Settings:** Execute `M500` to store the new parameters in EEPROM.

## Disclaimer
This configuration is tailored for the specific hardware mentioned above. Using this firmware on different boards or revisions may lead to hardware damage.