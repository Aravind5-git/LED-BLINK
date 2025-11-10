# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
<img width="1919" height="1145" alt="Screenshot 2025-11-11 001543" src="https://github.com/user-attachments/assets/bddf8300-e19c-4c0e-9f02-ac144d170fd5" />


2. Click **File → New STM32 Project**.
<img width="1919" height="1140" alt="Screenshot 2025-11-11 001724" src="https://github.com/user-attachments/assets/517bbeb6-334b-448f-9db9-a80636a0f1cd" />


3. Select the **target microcontroller** or board and click **Next**.
<img width="1919" height="1142" alt="Screenshot 2025-11-11 001903" src="https://github.com/user-attachments/assets/f5d5e158-dc0b-4e50-b7f5-ba7fa1057730" />



4. Name the project.
![WhatsApp Image 2025-11-10 at 20 11 50_c4ca29c9](https://github.com/user-attachments/assets/a4f09cfa-16b7-49c9-9dd0-081f0f15bd9f)


5. The corresponding `.ioc` file will be generated automatically.
![WhatsApp Image 2025-11-10 at 20 11 50_48336e74](https://github.com/user-attachments/assets/a16ab8fb-6fb0-4262-9a57-c8d734678666)


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
![WhatsApp Image 2025-11-10 at 20 11 50_984e8dfe](https://github.com/user-attachments/assets/3165f71f-338d-44c7-9099-2247f25f483b)


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
8. Edit the generated main program as required.
![WhatsApp Image 2025-11-10 at 20 11 53_9acf30c7](https://github.com/user-attachments/assets/052936fd-1bbd-47fb-b70a-5fd4cb3a1845)


9. Click **Project → Build All**.
![WhatsApp Image 2025-11-10 at 20 11 53_9acf30c7](https://github.com/user-attachments/assets/052936fd-1bbd-47fb-b70a-5fd4cb3a1845)

10. Link the **HEX file** using the post-build process.
![WhatsApp Image 2025-11-10 at 20 11 54_cafd0dad](https://github.com/user-attachments/assets/487b6936-9a39-4990-aac6-44bc60b14e1c)

11. Click **Debug** and connect the **STM Nucleo Board**.
![WhatsApp Image 2025-11-10 at 20 11 57_9c42090a](https://github.com/user-attachments/assets/536079f5-9d83-4dcd-9bd8-bbae690dbf65)


13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-11-10 at 20 16 36_dd3478a6](https://github.com/user-attachments/assets/498516c8-53de-44cf-8e70-9a22d651ffc5)


CASE 2: LED OFF
![WhatsApp Image 2025-11-10 at 20 16 35_b63f3e50](https://github.com/user-attachments/assets/119538c3-0bcc-4144-b801-516cd3d0968f)


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
