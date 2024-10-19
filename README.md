# ESP32-CAM Telegram Smart Lock System

This project implements a smart door lock system using the ESP32-CAM, allowing users to remotely control and monitor the lock via Telegram commands. It also integrates with ThingSpeak to log events such as photo captures and button presses. The system includes features like taking photos, locking/unlocking the door, and sending real-time data to ThingSpeak.

## Features
- **Control via Telegram**: Unlock/lock the door or request a photo via Telegram bot commands (`/unlock`, `/lock`, `/photo`).
- **ESP32-CAM Photo Capture**: Captures photos upon request or when the physical button is pressed.
- **ThingSpeak Integration**: Logs the timestamp of photo captures and the number of photos taken.
- **Button Interaction**: The system takes a photo when a button connected to the ESP32-CAM is pressed.
- **Flash Control**: Turns on the flash when taking photos for better image quality in low-light conditions.

## Components
- **ESP32-CAM**: Main microcontroller responsible for capturing images and controlling the solenoid lock.
- **Telegram Bot**: Allows for remote interaction with the system.
- **Solenoid Lock**: Acts as the door lock, controlled via GPIO.
- **ThingSpeak**: Logs event data for remote monitoring and analysis.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/safaeOulaja/Iot_DoorBell_with_Esp32CAM.git
   cd Iot_DoorBell_with_Esp32CAM
   ```

2. **Hardware Connections**:
   - **ESP32-CAM Pins**: Connect the pins as per the code configuration. GPIO 13 for the button, GPIO 12 for the solenoid lock, and GPIO 4 for the flash LED.
   - **Solenoid Lock**: Connect the solenoid lock to GPIO 12 for lock/unlock control.

3. **Modify the Code**:
   - Set your Wi-Fi credentials:
     ```cpp
     const char* ssid = "your-SSID";
     const char* password = "your-password";
     ```
   - Set your Telegram Bot Token and Chat ID:
     ```cpp
     String chatId = "your-chat-id"; 
     String BOTtoken = "your-bot-token";
     ```
   - Set your ThingSpeak API Key and Channel Number:
     ```cpp
     const char* myWriteAPIKey = "your-api-key"; 
     unsigned long myChannelNumber = your-channel-number;
     ```

4. **Install Required Libraries**:
   Install the following libraries in your Arduino IDE:
   - [WiFi](https://www.arduino.cc/reference/en/libraries/wifi/)
   - [WiFiClientSecure](https://www.arduino.cc/reference/en/libraries/wificlientsecure/)
   - [UniversalTelegramBot](https://github.com/witnessmenow/Universal-Arduino-Telegram-Bot)
   - [ArduinoJson](https://github.com/bblanchon/ArduinoJson)
   - [ThingSpeak](https://github.com/mathworks/thingspeak-arduino)

5. **Upload the Code**:
   Upload the code to your ESP32-CAM using the Arduino IDE.

6. **Use the Telegram Bot**:
   - `/start`: View available commands.
   - `/photo`: Capture and receive a photo from the ESP32-CAM.
   - `/unlock`: Unlock the door.
   - `/lock`: Lock the door.

## Future Improvements
- Add more security features like facial recognition.
- Add more functionalities.
- Improve error handling for unstable Wi-Fi connections.
