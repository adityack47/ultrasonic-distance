# Ultrasonic Distance Measurement using HC-SR04 and Arduino

This project demonstrates how to measure distance using an **HC-SR04 ultrasonic sensor** with an **Arduino**. The sensor calculates the time taken for an ultrasonic pulse to travel to an object and back, converting it into a distance measurement in **centimeters (cm)**.

## 📌 Features
- Uses an **HC-SR04** ultrasonic sensor to measure distance.
- Displays real-time distance readings on the **Serial Monitor**.
- Simple and efficient implementation using **Arduino C++**.

---

## 🛠 Components Required
| Component         | Quantity |
|------------------|----------|
| Arduino (Uno/Nano) | 1 |
| HC-SR04 Ultrasonic Sensor | 1 |
| Jumper Wires | 4 |

---

## ⚡ Circuit Connections
| HC-SR04 Pin | Arduino Pin |
|------------|------------|
| **VCC**    | 5V |
| **GND**    | GND |
| **Trig**   | 7 |
| **Echo**   | 6 |

---

## 🚀 Code
```cpp
// Ultrasonic Distance Measurement with HC-SR04
int distance = 0;

// Function to read distance using an ultrasonic sensor
long readUltrasonicDistance(int triggerPin, int echoPin) {
  pinMode(triggerPin, OUTPUT);
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  return pulseIn(echoPin, HIGH); // Returns time in microseconds
}

void setup() {
  Serial.begin(9600);
}

void loop() {
  distance = 0.01723 * readUltrasonicDistance(7, 6); // Convert time to cm

  Serial.print("Distance = ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(100); // 100ms delay for stable readings
}
