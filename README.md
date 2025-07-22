# Multi-Modal Free Space Optical (FSO) Communication System

This repository contains the hardware designs and software for a low-cost, multi-modal Free Space Optical (FSO) communication system developed for the EEE 310 course at Bangladesh University of Engineering & Technology (BUET). The system is capable of transmitting both analog and digital data wirelessly using a modulated laser beam.

![Project Preview1]([https://i.imgur.com/your-image-url.jpg](https://img.playbook.com/wTsnoP7YhVaTT7GavJLM8VVm8K8H-rpHjrOXgi0QnUw/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljLzE1MWI0NGQ4/LTQ4MWQtNGE0Ny1h/MWNmLWQzOTc3MzFk/MDhiMw))
![Project Preview2]((https://img.playbook.com/gjWpLh5UEJ70VvNFD718KViOndGVwJOB4LNx60tFzWo/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljL2E5NjJlNjky/LTI2MWUtNDVhYS05/MGM1LTk3YTFkMWEz/YjZmYQ))
*Replace the URL above with a link to an image of your project setup.*

---

## 📖 Abstract

This project demonstrates a versatile Free Space Optical (FSO) communication link that uses a laser to transmit various types of data through the air. The system leverages the high bandwidth and security of light-based communication to create a cost-effective wireless link. It supports two primary modes: analog audio transmission via Amplitude Modulation (AM) and digital data transmission using On-Off Keying (OOK). The digital mode is managed by ESP32 microcontrollers. This work covers the system's design, implementation, and performance, highlighting the feasibility of FSO for secure, short-range data links.

---
![Flow Diagram](https://img.playbook.com/jSCiHWhv9f0Vl6KF8J4FAy00vopyvy47CHvcUIU3PJw/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljL2QxM2ViYjRl/LTAxZTItNGUwMy1h/YjljLTVhZDMwMjNk/ODEzYQ)

## ✨ Features

This system integrates several communication modes into a single platform:

-   **Analog Audio Transmission**: Transmits real-time audio from a 3.5mm jack using amplitude modulation of the laser beam.
-   **Digital Text Transmission**: Sends ASCII text messages, which are decoded and displayed on an OLED screen at the receiver.
-   **Live Sensor Data**: Transmits real-time temperature data from a sensor on the transmitter.
-   **Remote Control**: Allows for remote adjustment of an LED's brightness on the receiver using a potentiometer on the transmitter.
-   **Mode Switching**: Physical switches on the transmitter allow for easy selection between different data transmission modes.

---

## ⚙️ How It Works

The system operates in two distinct modes, selected by a switch on the transmitter.

### 1. Analog Communication (Audio)
-   An analog audio signal from a microphone or audio jack is amplified.
-   The amplified signal modulates the intensity (amplitude) of the laser diode.
-   At the receiver, a solar panel detects these intensity variations and converts them back into an electrical signal.
-   This signal is then amplified to drive a speaker, reproducing the original audio.

### 2. Digital Communication (Text, Sensor, Control)
-   The transmitter-side ESP32 reads data (text, temperature, or potentiometer value) and encodes it into a binary format (8-bit ASCII).
-   It transmits this data using **On-Off Keying (OOK)**, where the laser is rapidly turned ON for a '1' and OFF for a '0'. An L293D motor driver is used as a robust switch to protect the ESP32's GPIO pin.
-   The receiver-side ESP32 uses a solar panel to detect the incoming light pulses. It measures the signal against a calibrated ambient light baseline to reconstruct the binary data.
-   The bits are reassembled into characters or values and displayed on the OLED screen or used to control the brightness of an LED.

---

## 🛠️ Hardware Components

| Component             | Transmitter                               | Receiver                                  |
| --------------------- | ----------------------------------------- | ----------------------------------------- |
| **Microcontroller** | ESP32                                     | ESP32                                     |
| **Light Source** | Laser Diode                               | -                                         |
| **Light Detector** | -                                         | Solar Panel                               |
| **Audio I/O** | MAX4466 Mic Amp, 3.5mm Audio Jack         | Speaker                                   |
| **Amplifier** | PAM8403                                   | PAM8403                                   |
| **Display** | -                                         | OLED Display (SSD1306, 128x64)            |
| **Driver/Switch** | L293D Motor Driver                        | -                                         |
| **User Input** | Potentiometer, SPDT Switches, Thermistor  | -                                         |
| **Power** | 9V Battery, 7805 Voltage Regulator        | 9V Battery, 7805 Voltage Regulator        |

---

## 🔌 Circuit Diagrams

### Transmitter Circuit
*(You should replace the link below with a direct link to your circuit diagram image in the repository)*
![Transmitter Circuit](https://img.playbook.com/02DOeo7H_QKNn6snM7zXj7mqPn6QE0nmTSzNm6aiaFY/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljLzZkZTNmODk5/LTgwNTktNDQwNS1i/ZmJkLWFhYTQwYjI5/MTAxMw)

### Receiver Circuit
*(You should replace the link below with a direct link to your circuit diagram image in the repository)*
![Receiver Circuit](https://img.playbook.com/edDrbgAukVNH3RLOAZbTAuzMcb-cS8myz0z4pM_QY-c/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljL2EwN2NjMTI2/LTllZjMtNDhhNy05/Y2E5LTNjYzM0YWJi/N2UzNA)

---

## 💻 Software & Setup

The code is developed using the Arduino IDE.

### Prerequisites
1.  **Arduino IDE**: Download and install from the [official website](https://www.arduino.cc/en/software).
2.  **ESP32 Board Support**: Follow [this guide](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html) to add ESP32 board support to your Arduino IDE.
3.  **Libraries**: Install the following libraries through the Arduino Library Manager (`Sketch > Include Library > Manage Libraries...`):
    -   `Adafruit GFX Library`
    -   `Adafruit SSD1306`

### Installation
1.  Clone this repository or download the source code.
2.  Open the `Transmitter/Transmitter.ino` file in the Arduino IDE.
3.  Connect the transmitter ESP32 to your computer.
4.  Select your board (`ESP32 Dev Module`) and the correct COM port from the `Tools` menu.
5.  Upload the code.
6.  Repeat steps 2-5 for the `Receiver/Receiver.ino` file and the receiver ESP32.

---

## 🚀 Usage

1.  Power on both the transmitter and receiver units.
2.  Carefully align the transmitter's laser so that it shines directly onto the receiver's solar panel.
3.  On the transmitter, use the switches to select the desired mode.
4.  Observe the output on the receiver's OLED display or listen for the audio from the speaker.

---

## 🚧 Challenges & Limitations

-   **Line-of-Sight**: The connection is strictly line-of-sight. Any physical obstruction will block the signal.
-   **Alignment**: Precise alignment between the laser and the solar panel is critical and can be difficult to maintain.
-   **Ambient Light**: Bright sunlight or other strong light sources can interfere with the receiver and corrupt the data.
-   **Range**: The practical range is limited due to beam divergence and detector sensitivity.

---

## 🌱 Future Improvements

-   **Error Correction**: Implement checksums or parity bits to improve the reliability of digital transmission.
-   **Auto-Alignment**: Develop a system with servo motors to automatically align the laser.
-   **Bidirectional Communication**: Add a second laser/detector pair to each unit for full-duplex communication.
-   **Faster Photodetector**: Replace the solar panel with a PIN photodiode for a faster, more linear response, enabling higher data rates.

---

## 👥 Authors

This project was a collaborative effort by:
-   **Md. Nazmus Sakib** (2106061)
-   **Abdullah Atif** (2106046)


### Under the Supervision of:
-   **Dr. Mohammad Faisal**, Professor, Dept. of EEE, BUET
-   **Archishman Sarkar**, Part-time Lecturer, Dept. of EEE, BUET
