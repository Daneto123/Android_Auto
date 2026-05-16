# DIY Android Auto & Infotainment System (Raspberry Pi 4)

This project outlines how to build a fully functional, DIY automotive infotainment system featuring **Android 14**, support for **Wireless Android Auto**, and integrated external **GPS navigation**.

## 🛠 Required Components
* **Raspberry Pi 4 (4GB RAM)** – The core computer of the system.
* **32GB SD Card (Class A2)** – High-speed card recommended for a smooth Android experience.
* **10.1" Touchscreen Display** (Model: `FT101DD348HD-50P`) with an HDMI controller.
* **5-Button Control Panel** – Hardware buttons mapped to GPIO pins for direct system control (Volume, Media, Home).
* **GNSS/GPS Module** – For precise real-time navigation using UART communication.
* **Power Converter (12V to 5V/3.5A)** – To ensure stable power delivery within the vehicle's electrical system.

## 💿 Software & OS
We are using the **LineageOS 21 (Android 14)** distribution by [KonstaKANG](https://konstakang.com/devices/rpi4/). 
Key benefits:
* **Full Android Experience:** Access to apps like YouTube, Spotify, and Waze.
* **Wireless Android Auto:** Enabled via the *Headunit Reloaded* app.
* **Hardware Acceleration:** Fully optimized for the Broadcom VideoCore VI.

## 🚀 Key Features & Optimizations
* **Smart Automation:** Bluetooth-triggered tethering. Once the phone connects to the Pi's Bluetooth, it automatically triggers a Wi-Fi Hotspot via Bixby Routines or Tasker.
* **Hardware Buttons:** 5 physical buttons configured via Device Tree Overlays (`gpio-keys`) for instant, interrupt-based response with 0% CPU overhead.
* **Integrated GPS:** Native GNSS data routing directly to the Android Location Service.
* **Performance Tweaks:** Customized `config.txt` to minimize boot time and force appropriate HDMI resolutions.

---

### 📖 Step-by-Step Instructions

#### 1. Software Preparation
1. Download the LineageOS 21 image.
2. Flash the image using **Raspberry Pi Imager**.
3. Edit `config.txt` in the boot partition to set your display resolution and enable GPIO overlays.

#### 2. Hardware Wiring (GPIO)
* **GPS Module:** * TX -> RX (Pin 10)
  * RX -> TX (Pin 8)
* **Control Buttons:** * Connect one side of all buttons to **GND**.
  * Connect the other side to GPIO pins **17, 27, 22, 23, 24**.

#### 3. Software Configuration
* Enable **UART** in the Raspberry Pi settings menu.
* Install **Headunit Reloaded (HUR)** for Wireless Android Auto functionality.
* Use **Aurora Store** for anonymous and lightweight app management.

# Additional Information
In order to support Android Auto or CarPlay, we need to enable screen mirroring from the phone. For this purpose, we will need two operating systems, because the specific board we currently have will not be sufficient on its own.
To achieve this, we will use PINN, which is a multi-boot system. The goal is to add Crankshaft to the current operating system and allow us, when the Raspberry Pi starts, to choose which of the two systems to use.
To support Android Auto, we will also need an additional external module.

## ⚖️ License
This project is for educational purposes. All software belongs to their respective owners.
