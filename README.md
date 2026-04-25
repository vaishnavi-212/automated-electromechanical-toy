# Automated Electromechanical Toy System

An interactive automated electromechanical toy developed using the ESP32 microcontroller. The system demonstrates controlled motion through the integration of DC motors and a servo motor, enabling coordinated actions based on programmed logic.

By combining embedded programming with motor actuation, the project showcases real-time control and automation in a compact and user-friendly design. The system focuses on simplicity, safety, and engaging interaction, making it suitable for practical and educational applications.

## Problem Statement

Modern toys often fail to balance **interactivity, safety, and usability**. Many existing products are either too complex for children, lack engaging features, or are not durable enough for regular use.

Common challenges include:

- Limited interaction and responsiveness  
- Complex or non-intuitive control systems  
- Poor durability under real-world usage  
- Use of unsafe or non-child-friendly materials  
- High cost for advanced functionality  

These limitations highlight the need for a toy that is **interactive, simple, durable, and cost-effective**, while still providing an engaging user experience.

## Project Objective

The objective of this project is to design and develop a **safe, interactive, and cost-effective automated electromechanical toy system**.

The system aims to:

- Provide engaging interaction through motion, light, and sound  
- Enable wireless control using Bluetooth communication  
- Ensure safety using non-toxic and child-friendly materials  
- Maintain durability to withstand minor impacts  
- Keep the design compact, portable, and easy to use  

The goal is to create a **balanced system** that integrates mechanical and electronic components while remaining simple, reliable, and accessible.

## Key Features

-  **Automated Motion Control**  
  Coordinated movement using DC motors and a servo motor based on programmed logic  

-  **Bluetooth-Based Wireless Control**  
  Real-time command execution using ESP32 Bluetooth communication  

-  **Interactive Behavior**  
  Combines motion, light, and response for an engaging user experience  

-  **Compact and Lightweight Design**  
  Easy to handle, portable, and suitable for children  

-  **Safe and User-Friendly System**  
  Designed with simple controls and child-safe materials  

-  **Efficient Power Usage**  
  Optimized design ensuring reliable performance with minimal energy consumption

##  System Architecture

The system is designed as an integration of three main subsystems:

###  Power Subsystem
- Provides power to all components using a 12V DC supply  
- A DC-DC buck converter steps down voltage to 5V for the servo motor  

###  Actuation Subsystem
- Two DC geared motors control rear wheel movement  
- A servo motor controls front wheel steering  
- Enables forward motion and directional control  

###  Control Subsystem
- ESP32 microcontroller acts as the central processing unit  
- Receives commands via Bluetooth  
- Processes input and controls motors accordingly  

These subsystems work together to achieve coordinated motion and real-time control.

##  Working Principle

The toy operates through Bluetooth-based wireless control using the ESP32 microcontroller.

- User sends commands from a mobile device  
- ESP32 processes the input in real time  
- DC motors drive movement  
- Servo motor controls steering  
- Commands are executed through programmed control logic  

This enables responsive automated motion and interactive operation.

##  Implementation Overview

- ESP32 used for control and Bluetooth communication  
- DC motors used for motion actuation  
- Servo motor used for steering control  
- Embedded code handles command processing and execution  

The implementation demonstrates real-time embedded automation in a compact electromechanical system.
## ESP32 Bluetooth LED Control

This project uses the ESP32 Bluetooth Serial feature to control the built-in LED using a mobile Bluetooth Terminal app.

### Features
- Connect to ESP32 via Bluetooth (`Vkkk`)
- Send `1` → LED ON  
- Send `0` → LED OFF  
##  Code

### Arduino Code

```cpp
#include "BluetoothSerial.h"

BluetoothSerial SerialBT;

#define LED_PIN 2   // Built-in LED on most ESP32 boards

void setup() {
  Serial.begin(115200);
  SerialBT.begin("Vkkk");   // Bluetooth device name
  pinMode(LED_PIN, OUTPUT);

  Serial.println("ESP32 Bluetooth ready. Pair and connect using Serial Bluetooth Terminal.");
}

void loop() {

  // Check Bluetooth connection
  if (SerialBT.hasClient()) {

    if (SerialBT.available()) {

      char incoming = SerialBT.read();   // Read Bluetooth data

      Serial.print("Received: ");
      Serial.println(incoming);

      if (incoming == '1') {
        digitalWrite(LED_PIN, HIGH);     // Turn LED ON
        SerialBT.println("LED ON");
        Serial.println("LED ON");
      }

      else if (incoming == '0') {
        digitalWrite(LED_PIN, LOW);      // Turn LED OFF
        SerialBT.println("LED OFF");
        Serial.println("LED OFF");
      }

      else {
        SerialBT.println("Send '1' to turn ON, '0' to turn OFF");
      }
    }
  }

  delay(100);   // Small delay for stability
}
```
##  Tech Stack

### Hardware
- ESP32 Microcontroller  
- 60 RPM DC Geared Motors  
- SG90 Servo Motor  
- Motor Driver Module  
- Bluetooth Communication Module (ESP32 inbuilt)  

### Software
- Embedded C / Arduino IDE  
- Bluetooth Serial Communication  
- Motor Control Logic  
- CAD Modeling for Design Development 

##  Results

- Successful Bluetooth-based control achieved  
- Real-time command execution validated  
- Motor and steering concept demonstrated  
- Compact automated prototype developed
