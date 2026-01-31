# Smart Bike Lock (IoT-Based Security System)

## 🎯 Project Description
The **Smart Bike Lock** is an embedded security system designed to prevent bicycle theft by providing real-time remote notification. While traditional locks are purely mechanical, this project adds an electronic "watchdog" layer that alerts the owner via a cellular network the moment the lock is tampered with or engaged.

### ⚙️ How It Works
The system utilizes an **Arduino** acting as the central processing unit and a **SIM800L GSM Module** for telecommunication.
1.  **Detection:** A switch (representing the lock state) is monitored by the microcontroller.
2.  **Communication:** Upon a trigger event, the microcontroller sends **AT commands** to the GSM module.
3.  **Alerting:** The GSM module initiates an **Automated Voice Call** to the owner's mobile number.

## 🚀 Features
* **Instant Alert:** Uses `ATD` commands to dial the owner's number immediately.
* **Debounced Logic:** Prevents multiple false-trigger calls using a `callMade` flag.
* **Fail-Secure:** Uses `INPUT_PULLUP` to ensure the system detects tampering reliably.

## 🛠️ Hardware Requirements
* **Microcontroller:** Arduino Uno (or compatible)
* **GSM Module:** SIM800L / SIM900
* **Sensor:** Limit switch / Push button
* **Power:** 5V/2A external supply (recommended for GSM)

## 🖇️ Pin Mapping
| Component | Arduino Pin | Function |
| :--- | :--- | :--- |
| GSM TX | Pin 7 | SoftwareSerial RX |
| GSM RX | Pin 8 | SoftwareSerial TX |
| Switch | Pin 2 | Input (Pull-up) |

## 💻 Software Logic
The system communicates using standard **AT Commands**:
* `AT`: Handshake to check module readiness.
* `ATD+91XXXXXXXXXX;`: Dials the phone number.
* `ATH`: Hangs up the call after 10 seconds.

## 🔧 Setup Instructions
1.  **Clone:** `git clone https://github.com/YOUR_USERNAME/smart-bike-lock.git`
2.  **Edit Number:** Open the `.ino` file and replace `+918951651606` with your number.
3.  **Upload:** Use the Arduino IDE to flash the code.
4.  **Monitor:** Open Serial Monitor at **9600 baud** to see the system status.
