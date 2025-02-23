# RISC-V Talent Development Program Powered by SAMSUNG and VSD
This is a RISC-V Internship using VSDSquadron Mini based  on RISC-V architecture and uses open-source tools to teach students about VLSI SoC design and RISC-V. The instructor and guide for this internship program is Mr. Kunal Ghosh, Co-Founder of VSD.

# ABOUT ME
Name: SUDHEEKSHA SK
-
College: Sahyadri College of Engineering and Management, Adyar, Mangaluru.
-
Email ID: sudheeksha.ec22@sahyadri.edu.in or sudeekshas36@gmail.com
-
LinkedIn: [Sudheeksha SK](https://www.linkedin.com/in/sudeeksha-s-b3a78626a?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)
-
<details>
<summary>TASK1:Development of C Based LAB</summary>
<img 
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/cbased%20lab%20output.png?raw=true" alt="Task Icon"/>
  <img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/cbased%20lab%20program.png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/leafpad%20installation.png?raw=true3" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/riscv%20based%20lab%20output(O1).png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/riscv%20based%20lab%20output(Ofast).png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/riscv%20based%20lab%20output.png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task1/riscv%20based%20lab.png?raw=true" alt="Task Icon"/>

</details>
<details>
<summary>TASK2:Simulation with Spike</summary>
<img 
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task2/debugging%2001.png?raw=true" alt="Task Icon"/>
  <img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task2/debugging%20Ofast.png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task2/objdump%20O1.png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task2/objdump%20Ofast.png?raw=true" alt="Task Icon"/>
<img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task2/program%20for%20task2(prod%20of%201%20to%205).png?raw=true" alt="Task Icon"/>
</details>

<details>
<summary>TASK3:Identification of RISCV instructions</summary>
  <img
src="https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%203/ofast%20objdump.png?raw=true" alt="Task Icon"/>
<summary># RISC-V Assembly Instructions Breakdown

## **1. `lui a0, 0x21`**  
**Opcode (U-Type):** `0110111`  
**Registers:** `rd = a0 (00101)`  
**Immediate:** `0x21 (0000000000100001)`  

| imm[31:12]  | rd (`a0`) | opcode  |
|-------------|---------|---------|
| 0000000000100001 | 00101 | 0110111 |

---

## **2. `addi sp, sp, -16`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = sp (00010)`, `rd = sp (00010)`  
**Immediate:** `-16 (1111111110000)`  

| imm[11:0] | rs1 (`sp`) | funct3 | rd (`sp`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 111111111000 | 00010 | 000 | 00010 | 0010011 |

---

## **3. `li a1, 120`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = zero (00000)`, `rd = a1 (00110)`  
**Immediate:** `120 (0000001111000)`  

| imm[11:0] | rs1 (`zero`) | funct3 | rd (`a1`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 0000001111000 | 00000 | 000 | 00110 | 0010011 |

---

## **4. `sd ra, 8(sp)`**  
**Opcode (S-Type):** `0100111`  
**Registers:** `rs1 = sp (00010)`, `rs2 = ra (00001)`  
**Immediate:** `8 (split as imm[11:5] = 0000000, imm[4:0] = 01000)`  

| imm[11:5] | rs2 (`ra`) | rs1 (`sp`) | funct3 | imm[4:0] | opcode  |
|-----------|-----------|-----------|--------|---------|---------|
| 0000000 | 00001 | 00010 | 011 | 01000 | 0100111 |

---

## **5. `jal ra, 10404`**  
**Opcode (J-Type):** `1101111`  
**Registers:** `rd = ra (00001)`  
**Immediate:** `10404 (split as imm[20] = 0, imm[19:12] = 00101000, imm[11] = 0, imm[10:1] = 0100000000)`  

| imm[20] | imm[10:1] | imm[11] | imm[19:12] | rd (`ra`) | opcode  |
|---------|-----------|--------|-----------|---------|---------|
| 0 | 0100000000 | 0 | 00101000 | 00001 | 1101111 |

---

## **6. `ld ra, 8(sp)`**  
**Opcode (I-Type):** `0000011`  
**Registers:** `rs1 = sp (00010)`, `rd = ra (00001)`  
**Immediate:** `8 (0000000001000)`  

| imm[11:0] | rs1 (`sp`) | funct3 | rd (`ra`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 0000000001000 | 00010 | 011 | 00001 | 0000011 |

---

## **7. `auipc a5, 0xffff0`**  
**Opcode (U-Type):** `0010111`  
**Registers:** `rd = a5 (01111)`  
**Immediate:** `0xffff0 (1111111111110000)`  

| imm[31:12] | rd (`a5`) | opcode  |
|------------|---------|---------|
| 1111111111110000 | 01111 | 0010111 |

---

## **8. `ori s1, s1, 1`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = s1 (10001)`, `rd = s1 (10001)`  
**Immediate:** `1 (0000000000001)`  

| imm[11:0] | rs1 (`s1`) | funct3 | rd (`s1`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 0000000000001 | 10001 | 110 | 10001 | 0010011 |

---

## **9. `sext.w s1, s1`** 
**Opcode (I-Type):** `0011011`  
**Registers:** `rs1 = s1 (10001)`, `rd = s1 (10001)`  
**Immediate:** `0 (0000000000000)`  

| imm[11:0] | rs1 (`s1`) | funct3 | rd (`s1`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 000000000000 | 10001 | 000 | 10001 | 0011011 |

---

## **10. `andi a3, s1, 1024`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = s1 (10001)`, `rd = a3 (00011)`  
**Immediate:** `1024 (000001000000)`  

| imm[11:0] | rs1 (`s1`) | funct3 | rd (`a3`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 000001000000 | 10001 | 111 | 00011 | 0010011 |


---

## **11. `lw a0, 0(sp)`**  
**Opcode (I-Type):** `0000011`  
**Registers:** `rs1 = sp (00010)`, `rd = a0 (00101)`  
**Immediate:** `0 (000000000000)`  

| imm[11:0] | rs1 (`sp`) | funct3 | rd (`a0`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 000000000000 | 00010 | 010 | 00101 | 0000011 |

---

## **12. `add a5, a4, a5`**  
**Opcode (R-Type):** `0110011`  
**Registers:** `rs1 = a4 (00100)`, `rs2 = a5 (01111)`, `rd = a5 (01111)`  

| funct7 | rs2 (`a5`) | rs1 (`a4`) | funct3 | rd (`a5`) | opcode  |
|--------|-----------|-----------|--------|---------|---------|
| 0000000 | 01111 | 00100 | 000 | 01111 | 0110011 |

---

## **13. `jalr zero`**  
**Opcode (I-Type):** `1100111`  
**Registers:** `rs1 = zero (00000)`, `rd = zero (00000)`  
**Immediate:** `0 (000000000000)`  

| imm[11:0] | rs1 (`zero`) | funct3 | rd (`zero`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 000000000000 | 00000 | 000 | 00000 | 1100111 |

---

## **14. `srai a3, a3, 0x3f`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = a3 (00011)`, `rd = a3 (00011)`  
**Immediate:** `0x3f (0111111)`  

| funct7 | shamt (`0x3f`) | rs1 (`a3`) | funct3 | rd (`a3`) | opcode  |
|--------|--------------|-----------|--------|---------|---------|
| 0100000 | 011111 | 00011 | 101 | 00011 | 0010011 |

---

## **15. `not a3, s0`**  
**Opcode (I-Type):** `0010011`  
**Registers:** `rs1 = s0 (01000)`, `rd = a3 (00011)`  
**Immediate:** `-1 (111111111111)`  

| imm[11:0] | rs1 (`s0`) | funct3 | rd (`a3`) | opcode  |
|-----------|-----------|--------|---------|---------|
| 111111111111 | 01000 | 100 | 00011 | 0010011 |

---
## **16. `sub a2, a2, a0`**  
**Opcode (R-Type):** `0110011`  
**Registers:** `rs1 = a0 (00101)`, `rs2 = a2 (00110)`, `rd = a2 (00110)`  

| funct7 | rs2 (`a0`) | rs1 (`a2`) | funct3 | rd (`a2`) | opcode  |
|--------|-----------|-----------|--------|---------|---------|
| 0100000 | 00101 | 00110 | 000 | 00110 | 0110011 |
</details>
<details>
<summary>TASK4:Functional Simulation of RISC-V Core</summary>
</summary>
<br>
Steps to perform functional simulation of RISCV

1. Download Files:
Download the code from the reference github repo.

2. Set Up Simulation Environment:
Install iverlog using commands:

        sudo apt install iverilog
        sudo apt install gtkwave

3. To run and simulate the verilog code, enter the following command:

        iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
        ./iiitb_rv32i

4. To see the simulation waveform in GTKWave, enter the following command:

        gtkwave iiitb_rv32i.vcd

32-bits instruction used in the code:

![Instructions](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/instruction.png?raw=true>)

Analysing the Output Waveform of various instructions that we have covered in this task.

1. ADD R6,R1,R2

![ADD R6,R1,R2](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/add.png?raw=true>)

  32 bit instruction:32'h02208300

2. SUB R7,R1,R2

![SUB R7,R1,R2](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/sub1.png?raw=true>)

32 bit instruction:32'h02209380

3. And R8,R1,R3

![And R8,R1,R3](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/and.png?raw=true>)

32 bit instruction:32'h0230a400

4. OR R9,R2,R5

![OR R9,R2,R5](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/or.png?raw=true>)

32 bit instruction:32'h02513480

5. XOR R10,R1,R4

![XOR R10,R1,R4](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/xor.png?raw=true>)

32 bit instruction:32'h0240c500

6. SLT R11,R2,R4

![SLT R11,R2,R4](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/slt.png?raw=true>)

32 bit instruction:32'h02415580

7. ADDI R12,R4,5

![ADDI R12,R4,5](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/addi.png?raw=true>)

32 bit instruction:32'h00520600

8. BEQ R0,R0,15

![BEQ R0,R0,15](<https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/blob/main/task%204/beq.png?raw=true>)

32 bit instruction:32'h00f00002

</details>

<details>
<summary>TASK5:Project overview-circuit diagram</summary>
</summary>
1.Pinout Diagram of Obstacle-Avoiding Robot
<img 
src="https://github.com/user-attachments/assets/0828d309-aa0c-45bc-8cce-038ce368d9bf" alt="Task Icon"/>
<img

2.Blinking Led Test code simulation.

https://github.com/Sudheeksha-Sahyadri-ECE/samsung-riscv/raw/refs/heads/main/task%205/blinking_led_test.mp4
</details>

<details>
<summary>TASK6:Project Application</summary>
</summary>
1.Object detection and Alert system Application video.

https://github.com/user-attachments/assets/11397a90-0576-4397-b83f-7a6ea71d9968

2.Obstacle-Avoiding Robot Code.
```
#include <ch32v00x.h>
#include <debug.h>

// Define motor control pins
#define IN1_PIN GPIO_Pin_1
#define IN2_PIN GPIO_Pin_2
#define IN3_PIN GPIO_Pin_4
#define IN4_PIN GPIO_Pin_7
#define ENA_PIN GPIO_Pin_5 // Assuming ENA is connected to PA0 (PWM), not necessary
#define ENB_PIN GPIO_Pin_6 // Assuming ENB is connected to PA1 (PWM), not necessary

// Define PIR sensor pin
#define PIR_PIN GPIO_Pin_3

void Motor_Init(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};

    // Enable clocks for GPIO ports
    
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD | RCC_APB2Periph_GPIOA, ENABLE);

    // Configure motor control pins as outputs
    
    GPIO_InitStructure.GPIO_Pin = IN1_PIN | IN2_PIN | IN3_PIN | IN4_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Configure ENA and ENB pins as alternate function (PWM output)
    GPIO_InitStructure.GPIO_Pin = ENA_PIN | ENB_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_AF_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOA, &GPIO_InitStructure);

    // Initialize PWM for ENA and ENB
    // Assuming TIM2 is used for PWM on PA0 and PA1
    RCC_APB1PeriphClockCmd(RCC_APB1Periph_TIM2, ENABLE);

    TIM_TimeBaseInitTypeDef TIM_TimeBaseStructure = {0};
    TIM_OCInitTypeDef TIM_OCInitStructure = {0};

    TIM_TimeBaseStructure.TIM_Period = 999;
    TIM_TimeBaseStructure.TIM_Prescaler = 47;
    TIM_TimeBaseStructure.TIM_ClockDivision = TIM_CKD_DIV1;
    TIM_TimeBaseStructure.TIM_CounterMode = TIM_CounterMode_Up;
    TIM_TimeBaseInit(TIM2, &TIM_TimeBaseStructure);

    TIM_OCInitStructure.TIM_OCMode = TIM_OCMode_PWM1;
    TIM_OCInitStructure.TIM_OutputState = TIM_OutputState_Enable;
    TIM_OCInitStructure.TIM_Pulse = 500; // 50% duty cycle
    TIM_OC1Init(TIM2, &TIM_OCInitStructure);
    TIM_OC2Init(TIM2, &TIM_OCInitStructure);

    TIM_Cmd(TIM2, ENABLE);
}

void PIR_Init(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};

    // Enable clock for GPIOD
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);

    // Configure PIR sensor pin as input pull-up
    GPIO_InitStructure.GPIO_Pin = PIR_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
}

void Move_Forward(void) {
    GPIO_SetBits(GPIOD, IN1_PIN);
    GPIO_ResetBits(GPIOD, IN2_PIN);
    GPIO_SetBits(GPIOD, IN3_PIN);
    GPIO_ResetBits(GPIOD, IN4_PIN);
}

void Move_Backward(void) {
    GPIO_ResetBits(GPIOD, IN1_PIN);
    GPIO_SetBits(GPIOD, IN2_PIN);
    GPIO_ResetBits(GPIOD, IN3_PIN);
    GPIO_SetBits(GPIOD, IN4_PIN);
}

void Turn_Left(void) {
    GPIO_ResetBits(GPIOD, IN1_PIN);
    GPIO_SetBits(GPIOD, IN2_PIN);
    GPIO_SetBits(GPIOD, IN3_PIN);
    GPIO_ResetBits(GPIOD, IN4_PIN);
}

void Turn_Right(void) {
    GPIO_SetBits(GPIOD, IN1_PIN);
    GPIO_ResetBits(GPIOD, IN2_PIN);
    GPIO_ResetBits(GPIOD, IN3_PIN);
    GPIO_SetBits(GPIOD, IN4_PIN);
}

void Stop(void) {
    GPIO_ResetBits(GPIOD, IN1_PIN | IN2_PIN | IN3_PIN | IN4_PIN);
}

int main(void) {
    SystemCoreClockUpdate();
    Delay_Init();
    Motor_Init();
    PIR_Init();

    while (1) {
        uint8_t pir_status = GPIO_ReadInputDataBit(GPIOD, PIR_PIN);

        if (pir_status == 0) {
            // Obstacle detected
            Stop();
            Delay_Ms(500);
            Move_Backward();
            Delay_Ms(1000);
            Turn_Left();
            Delay_Ms(500);
            Stop();
            Delay_Ms(500);
        } else {
            // No obstacle
            Move_Forward();
        }

        Delay_Ms(100);
    }
}

void NMI_Handler(void) {
}

void HardFault_Handler(void) {
    while (1) {
    }
}
