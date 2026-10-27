# ESP32-S3 Development Board

A professional-grade, high-performance **ESP32-S3 Development Board**. This hardware implementation uses a 4-layer PCB stackup to optimize signal integrity, accommodate controlled-impedance differential USB paths, and provide a low-noise ground reference for the RF module's wireless performance. I needed the ESP32-S3 for many projects, and it's dev kits were out of stock or too expensive locally. So, I challenged myself to build a Dev Board for it myself, and in the same formfactor as that of Espressif, without compromising on signal integrity or double side component placement. 

## Features
* **Core Processor:** ESP32-S3-MINI-1
* **Dual USB Type-C Connectivity:** 
  * **USB OTG Port:** Direct native connection to the ESP32-S3 USB pins (IO19/IO20) for USB Host/Device applications.
  * **USB to UART Port:** Uses a CP2102N in order to get a secondary USB port.
* **Automated Boot Circuit:** Dual NPN transistor (L8050QLT1G) circuit for hands-free flashing and reset toggling via DTR/RTS signals.
* **Power & Protection:** 
  * Linear LDO regulation (**LD1117S33TR**) providing up to 800mA on the 3.3V rail.
  * Input overcurrent protection via a resettable PPTC Polyfuse.
  * Transient Voltage Suppression (TVS) arrays on all VBUS, CC, and USB Data lines to prevent ESD damage.
* **Peripherals & Debugging:**
  * One addressable **SK6812MINI RGB LED** on GPIO 48 for multi-color status indication.
  * User-accessible Boot (IO0) and Reset tactile pushbuttons.
  * Dedicated test points for high-level JTAG debugging (TMS, TCK, TDO, TDI).
  * Two 23-pin expansion headers exposing extensive GPIO arrays, power rails, and ground pins.

## Stackup Configuration
This project utilizes a standard **4-layer stackup** designed to minimize electromagnetic interference (EMI) and provide solid reference planes for the high-frequency RF layout.

*Traces assigned to `USB_OTG` and `USB_UART` lines are routed as **90Ω differential pairs**.

## Hardware Component Configuration

### Power System
* **Input Options:** Powered via the Native USB-C port, UART USB-C port, or the external expansion headers (+5V).
* **Indicator:** An on-board yellow-green LED (`3216SYGC`) provides immediate visual confirmation of a stable 3.3V power rail.

## Manufacturing & Assembly Notes (for maintained differential pair impedance)
* **PCB Thickness:** 1.6 mm
* **Material:** FR-4 (High TG150+ recommended due to the RF component thermal profile)

<img width="1152" height="905" alt="ESP32 S3 dev board schematic" src="https://github.com/user-attachments/assets/1e120d9b-bf93-4f5b-b2d1-4f4329e113f9" />

<img width="1152" height="648" alt="ESP32 S3" src="https://github.com/user-attachments/assets/e6115d3e-af28-4fec-9da3-ca13b3086132" />
