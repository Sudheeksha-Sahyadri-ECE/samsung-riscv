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

## **Code for VSDSquadron Mini Board**
```c
#include <vsdsquadron.h>  // Include VSDSquadron Mini Board hardware headers

#define TRIG_PIN  GPIO_Pin_0  // GPIO0 for Trigger
#define ECHO_PIN  GPIO_Pin_1  // GPIO1 for Echo
#define LED_PIN   GPIO_Pin_2  // GPIO2 for LED
#define BUZZER_PIN GPIO_Pin_3 // GPIO3 for Buzzer

void delay_us(uint32_t us) {
    for (volatile uint32_t i = 0; i < us * 8; i++) {
        __NOP();  // Small delay for microseconds
    }
}

void delay_ms(uint32_t ms) {
    for (volatile uint32_t i = 0; i < ms * 8000; i++) {
        __NOP();
    }
}

uint32_t measure_distance() {
    uint32_t time_count = 0;

    // Send 10µs pulse to TRIG pin
    GPIO_SetBits(GPIO0, TRIG_PIN);
    delay_us(10);
    GPIO_ResetBits(GPIO0, TRIG_PIN);

    // Wait for Echo Pin to go HIGH
    while (!GPIO_ReadInputDataBit(GPIO1, ECHO_PIN));

    // Start counting while Echo is HIGH
    while (GPIO_ReadInputDataBit(GPIO1, ECHO_PIN)) {
        time_count++;
        delay_us(1);
    }

    // Convert time to distance (Speed of sound = 343m/s)
    return (time_count * 0.0343) / 2;  // Distance in cm
}

int main(void) {
    SystemInit();  // Initialize system clock

    // Enable GPIO Clock
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIO, ENABLE);

    // Configure TRIG, LED, and BUZZER as output
    GPIO_InitTypeDef GPIO_InitStruct;
    GPIO_InitStruct.GPIO_Pin = TRIG_PIN | LED_PIN | BUZZER_PIN;
    GPIO_InitStruct.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStruct.GPIO_Speed = GPIO_Speed_10MHz;
    GPIO_Init(GPIO0, &GPIO_InitStruct);

    // Configure ECHO as input
    GPIO_InitStruct.GPIO_Pin = ECHO_PIN;
    GPIO_InitStruct.GPIO_Mode = GPIO_Mode_IN_FLOATING;
    GPIO_Init(GPIO1, &GPIO_InitStruct);

    while (1) {
        uint32_t distance = measure_distance();

        // If distance is less than 10 cm, turn LED and Buzzer ON
        if (distance < 10) {
            GPIO_SetBits(GPIO2, LED_PIN);
            GPIO_SetBits(GPIO3, BUZZER_PIN);
        } else {
            GPIO_ResetBits(GPIO2, LED_PIN);
            GPIO_ResetBits(GPIO3, BUZZER_PIN);
        }

        delay_ms(500);  // Delay to avoid continuous measurements
    }
}
