## **Code**
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
