# **Object Detection and Alert system with VSDSquadron Mini Board**

## **Project Name**
**Object Detection with LED & Buzzer Alert Using VSDSquadron Mini Board**

---

## **Overview**
This project demonstrates **real-time object detection** using an **HC-SR04 Ultrasonic Sensor** with the **VSDSquadron Mini Board**. When an object is detected within **10 cm**, an **LED and a buzzer turn ON**, providing an **audio-visual alert**. The system operates at **3.3V**, making it efficient and compatible with low-power applications.

### **Applications**
- **Proximity sensing** for robotics and automation.
- **Obstacle detection** for smart vehicles and drones.
- **Security systems** for intruder detection.
- **Smart home automation** (e.g., automatic door opening).

---

## **Components Required**
| **Component** | **Quantity** | **Description** |
|--------------|------------|----------------|
| **VSDSquadron Mini Board** | 1 | RISC-V-based microcontroller board |
| **HC-SR04 Ultrasonic Sensor** | 1 | Measures distance using sound waves |
| **LED** | 1 | Indicates object detection |
| **Buzzer** | 1 | Provides an alert sound |
| **Jumper Wires** | 6+ | Connects components |
| **Breadboard** | 1 | For easy circuit prototyping |
| **3.3V Power Supply** | 1 | Powers the circuit |

---

## **Circuit Connections (3.3V)**
| **HC-SR04 Pin** | **VSDSquadron Mini Board Pin** |
|----------------|-------------------------------|
| **VCC** | **3.3V** |
| **GND** | **GND** |
| **TRIG** | **GPIO0 (PC0)** |
| **ECHO** | **GPIO1 (PC1)** |

| **Component** | **VSDSquadron Mini Board Pin** |
|--------------|-------------------------------|
| **LED** | **GPIO2 (PC2)** |
| **Buzzer** | **GPIO3 (PC3)** |

---

## **Working Mechanism**
1. **The VSDSquadron Mini Board sends a trigger pulse** to the **HC-SR04 Ultrasonic Sensor**.
2. The sensor sends out an **ultrasonic wave** and waits for its reflection.
3. The **ECHO pin remains HIGH** for a duration proportional to the distance.
4. The **code calculates the distance** based on the time measured.
5. If the object is **within 10 cm**, the **LED and Buzzer turn ON**.
6. If the object is **farther than 10 cm**, the **LED and Buzzer turn OFF**.
7. A **500ms delay** prevents **continuous triggering**.

---



## **Conclusion**
This project involved designing and implementing a simple circuit using the CH32V003 RISC-V board. The system utilized LEDs and a buzzer to demonstrate GPIO control and peripheral interfacing. Through this project, I successfully developed and tested a functional setup, ensuring efficient operation and responsiveness of the components.**.

---

