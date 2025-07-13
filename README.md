# Light Sensor(LDR) LED Control using Arduino

This project demonstrates how to control an LED based on ambient light using an **LDR (Light Dependent Resistor)** and an **Arduino Uno**. When it's dark, the LED turns on. When there's enough light, the LED turns off automatically.

## 📷 Project Media

- 📸 **Image of Circuit**  
  ![Circuit Diagram](https://github.com/JawaherMQ5/LDR/blob/main/Screenshot%202025-07-13%20115739.png)

- 🎥 **Demo Video**  
 https://drive.google.com/file/d/1MSWBitIA9EinSfF-9VPTtDQ60T4i3LZ_/view?usp=drivesdk
## 🔧 Components Used

- 1 x Arduino Uno  
- 1 x Breadboard  
- 1 x LDR (Light Dependent Resistor)  
- 1 x LED  
- 2 x Resistors (220Ω for LED, 10kΩ for LDR voltage divider)  
- Jumper Wires  
- USB cable for Arduino

## 🔌 Circuit Explanation

- The **LDR** is connected in a voltage divider circuit with a 10kΩ resistor.
- The analog output of the LDR is read from pin **A0**.
- The **LED** is connected to pin **D13** through a 220Ω resistor.
- When the light level drops below a certain threshold (e.g., at night), the LED turns on.

## 🧠 Arduino Code

```cpp
int ldrPin = A0;        // LDR connected to A0
int ledPin = 13;        // LED connected to D13
int threshold = 500;    // Light threshold (adjust as needed)

void setup() {
  pinMode(ledPin, OUTPUT);    // Set LED pin as output
  Serial.begin(9600);         // Start serial monitor
}

void loop() {
  int lightValue = analogRead(ldrPin);  // Read light level
  Serial.println(lightValue);           // Print value for debugging

  if (lightValue < threshold) {
    digitalWrite(ledPin, HIGH);  // It's dark ➜ turn LED on
  } else {
    digitalWrite(ledPin, LOW);   // Bright enough ➜ turn LED off
  }

  delay(200);  // Small delay
}
