# ESP32 Evil Twin WiFi Hacking: Deauthentication & Captive Portal 🛰️🔓

**Disclaimer**: This project is for **educational purposes only**. Unauthorized use is illegal. Only test on networks you own.  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📜 Overview  
This project demonstrates an **Evil Twin attack** using an ESP32 microcontroller. It combines a deauthentication attack to disconnect devices from a target WiFi network and a captive portal to capture credentials via a rogue access point.

---

## 🚀 Features  
- **Deauthentication Attack**: Forces devices offline using forged WiFi packets.  
- **Rogue Access Point**: Spoofs the target network's SSID.  
- **Captive Portal**: Fake login page (HTML/CSS/JS) to harvest credentials.  
- **ESP32 Integration**: Low-cost IoT device for penetration testing.  

---

## 📦 Prerequisites  
### Hardware  
- ESP32 development board (e.g., ESP32-WROOM-32).  
- USB cable (for power/programming).  

### Software  
- [Arduino IDE](https://www.arduino.cc/en/software)  
- [ESP32 Board Support](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html)  
- Libraries:  
  - `ESPAsyncWebServer`  
  - `AsyncTCP`  
  - `DNSServer`  

---

## 🛠️ Setup Guide  

### 1. Install Arduino IDE & ESP32 Core  
1. Open Arduino IDE → **File → Preferences**.  
2. Add this URL to **Additional Boards Manager URLs**:


3. Install the ESP32 board:  
- **Tools → Board → Boards Manager** → Search "ESP32" → Install.  

### 2. Clone the Repository  

git clone https://github.com/yourusername/esp32-evil-twin.git  
cd esp32-evil-twin


3. Install Required Libraries

In Arduino IDE:
Sketch → Include Library → Manage Libraries → Install:
ESPAsyncWebServer
AsyncTCP
4. Configure Target Network

Open esp32_deauth_attack.ino.
Set the target SSID and BSSID (MAC address):
cpp
// ====== TARGET NETWORK ======  
const char* evil_ssid = "Legitimate_WiFi_Name"; // Replace with target SSID  
uint8_t target_bssid[] = {0x12, 0x34, 0x56, 0x78, 0x9A, 0xBC}; // Replace with target router's MAC  
To find the BSSID:
Use the scanNetworks() function in the code (check Serial Monitor).
5. Customize the Captive Portal

Edit files in the html/ folder:
index.html: Modify the login page design.
style.css: Adjust styling to mimic a legitimate portal.
script.js: Handle form submissions.
6. Upload the Code

Connect the ESP32 via USB.
Select board: Tools → Board → ESP32 Dev Module.
Select port: Tools → Port.
Click Upload (➡️ icon).
⚡ Executing the Attack

1. Start the Evil Twin AP

The ESP32 will broadcast a rogue AP with the target SSID.
2. Launch Deauthentication Attack

The ESP32 sends deauthentication packets to disconnect devices from the legitimate network.
3. Capture Credentials

Users connecting to the rogue AP are redirected to the captive portal.
Credentials are logged in the Serial Monitor (Baud Rate: 115200).
📁 Project Structure

esp32-evil-twin/  
├── esp32_deauth_attack.ino  # Main ESP32 code  
├── html/                    # Captive portal files  
│   ├── index.html  
│   ├── style.css  
│   └── script.js  
├── LICENSE  
└── README.md  
🔧 Troubleshooting

AP Not Visible: Ensure evil_ssid matches the target SSID exactly.
Deauth Failing: Verify the BSSID is correct and the ESP32 is in range.
Portal Not Loading: Check DNS server configuration in setup().
