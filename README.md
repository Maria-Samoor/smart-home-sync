# Smart Home Sync

## Project Overview

This project, named **Smart Home Sync**, involves the synchronization and communication between an ESP32 and an ESP8266 microcontroller, each managing different sensors and actuators. The project aims to create a smart home system with various functionalities, including temperature control, light detection, motion detection, distance measurement, and door access control, all integrated with Amazon Alexa for voice control. Additionally, Arduino Cloud is used for device management and data visualization.

## Components Used

### Hardware Components
- **ESP8266**:
  - DHT Sensor: Measures temperature and humidity.
  - LCD Display: Displays the temperature readings.
  - LDR Sensor: Detects ambient light levels.
  - Ultrasonic Sensor: Measures distance to objects.
  - Servo Motor: Controls the door mechanism.
  - 2 LEDs: Controlled by motion detection from ESP32.
  
- **ESP32**:
  - DC Motor: Activates based on temperature readings.
  - LED: Lights up based on LDR sensor readings.
  - Motion Sensor: Detects motion to control LEDs on ESP8266.
  - Buzzer: Activates based on ultrasonic sensor and RFID readings.
  - RFID Reader: Validates tags to control the buzzer and servo motor.

### Software Components
- **Arduino IDE**: Used for programming the ESP8266 and ESP32.
- **Arduino Cloud**: For device management and data visualization.
- **Amazon Alexa**: For voice control integration.
- **MQTT Protocol**: For communication between ESP8266 and ESP32.
- **Arduino Libraries**: Various libraries for sensors, actuators, and communication.

## Functionality

### Temperature Control
- The ESP8266 reads temperature from the DHT sensor and displays it on the LCD.
- If the temperature exceeds 23.5°C, this information is sent to the ESP32.
- The ESP32 activates a DC motor if the temperature is greater than 23.5°C.

### Light Detection
- The LDR sensor on the ESP8266 detects the light level.
- If the light level is ≤300, this information is sent to the ESP32.
- The ESP32 lights up an LED based on the LDR sensor value.

### Motion Detection
- The ESP32 uses a motion sensor to detect movement.
- If motion is detected, the ESP8266 will turn on two LEDs.
- Both the LEDs and motion sensor can be controlled via Amazon Alexa.

### Distance Measurement
- The ultrasonic sensor on the ESP8266 measures the distance to nearby objects.
- If the distance is less than 6 cm, this information is sent to the ESP32.
- The ESP32 activates a buzzer based on the distance measurement.

### Door Access Control
- An RFID reader on the ESP32 validates tags.
- If the tag is correct, the ESP32 activates a buzzer and sends a signal to the ESP8266 to open the door using the servo motor.
- If the tag is incorrect, a different buzzer tone is activated.
- The door (servo motor) can also be controlled via Amazon Alexa.

## Setup and Installation

### Hardware Setup
1. Connect the DHT sensor, LCD, LDR sensor, ultrasonic sensor, and servo motor to the ESP8266 as per their respective pin configurations.
2. Connect the DC motor, LED, motion sensor, buzzer, and RFID reader to the ESP32 as per their respective pin configurations.

### Software Setup
1. Flash the ESP8266 and ESP32 with the provided Arduino sketches.
2. Ensure that both microcontrollers are connected to the same Wi-Fi network for communication.
3. Configure the Arduino Cloud for device management and data visualization.
4. Configure the Amazon Alexa skills for voice control of the LEDs, motion sensor, and door.

### Synchronization
- Use the MQTT protocol or HTTP communication to synchronize data between the ESP8266 and ESP32.
- Implement the required logic in the Arduino sketches to handle the synchronization and control mechanisms.

## Usage

1. Power on both the ESP8266 and ESP32.
2. The system will start reading sensor values and controlling actuators based on the logic described above.
3. Use Amazon Alexa to control the LEDs, motion sensor, and door mechanism via voice commands.

## Troubleshooting
- Ensure both microcontrollers are on the same Wi-Fi network.
- Check sensor and actuator connections.
- Verify MQTT or HTTP communication is correctly set up.
- Use serial monitor to debug sensor readings and communication issues.

## Future Improvements

- Add more sensors and actuators for additional smart home functionalities.
- Improve the user interface on the LCD display.
- Enhance the security of the RFID access control system.
