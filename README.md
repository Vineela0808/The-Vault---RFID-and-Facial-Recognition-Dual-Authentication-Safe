# The-Vault---RFID-and-Facial-Recognition-Dual-Authentication-Safe
## Abstract
The Vault is a smart safe system integrating a dual-layered authentication mechanism that combines RFID verification and facial recognition to maximize security. Designed for high-security applications, the system ensures that only authorized users can access the contents of the safe. The process begins with RFID-based identification followed by facial verification using a camera and Raspberry Pi. A custom 3D-printed safe, secured with a servo-based locking mechanism, completes the hardware interface. With visual and auditory feedback at every step, this project offers a modern, efficient, and intuitive approach to securing physical assets.
## System Overview
The user initiates authentication by tapping their RFID card on a reader. The Arduino Uno verifies the tag using SPI communication with the RC522 module. If the RFID is valid, the Raspberry Pi triggers a camera to capture the user’s face. Facial recognition is performed and the result is sent back to the Arduino via UART over USB Serial (CDC ACM). If both steps succeed, the Arduino unlocks the safe using a servo motor and logs the access event with audio-visual feedback.
## Components Used
- Arduino Uno – Handles RFID scanning, servo control, and communication with Raspberry Pi
- Raspberry Pi 4 – Captures and processes facial recognition via a camera module
- RC522 RFID Module – Reads RFID tags (communicates with Arduino via SPI)
- Raspberry Pi Camera V3 – Captures facial image for comparison
- 7" HDMI Display – Provides visual feedback (e.g., "Access Denied")
- Servo Motor – Operates the locking mechanism
- Piezo Buzzer – Provides sound alerts for success/failure
- Power Supply – 6V for servo + 5V for logic
- Custom 3D-Printed Safe Enclosure
## Key Features
- **Dual-Layer Security**: Combines RFID card identification and real-time facial recognition for robust access control.
- **Real-Time Feedback**:
  - Buzzer alerts signal authentication success or failure.
  - Screen messages indicate stages like “Access Denied” or “Access Granted”
- **Custom 3D Safe** : A fully designed, printed, and assembled physical housing secures the internal electronics and valuables.
- **SPI Communication** : The RC522 RFID module interfaces with the Arduino Uno via the SPI protocol, enabling fast and secure transmission of card UID data for authentication.
- **Modular Electronics** : Raspberry Pi handles facial recognition; Arduino controls servo and RFID. The two communicate via UART for seamless coordination.
- **Image Logging & Access History** : The system logs access attempts with timestamps and identification results for future auditability.
## Working Pattern
- **System Boot** : Initializes all components including RFID, camera, and display
- **RFID Authentication** :The user taps their RFID card. The Arduino reads the card’s UID via SPI, verifies it, and transmits the authentication result to the Raspberry Pi via UART.
- **Facial Recognition** : Upon receiving a valid RFID result, the Raspberry Pi captures the user's face using a CSI camera. It then compares the captured image with stored images using the OpenCV SDK. If a match is found, it sends an 'R' signal back to the Arduino via serial communication.
- **Unlocking Mechanism** : Upon receiving the 'R' signal, the Arduino activates the servo motor to unlock the safe. The system logs the event and provides both audio and visual feedback to confirm successful access.
  
