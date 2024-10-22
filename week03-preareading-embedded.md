# Embedded development prereading

**Embedded development** refers to the process of designing, programming, and maintaining software that is specifically built to run on **embedded systems**. Embedded systems are specialized computing devices that are part of a larger mechanical or electrical system, designed to perform dedicated functions or tasks. Examples include microcontrollers in household appliances, automotive systems, medical devices, or industrial machines.

Key characteristics of embedded development:

-   The software interacts directly with the hardware.
-   It often has strict performance, real-time, and memory constraints.
-   The development process requires knowledge of both hardware and software.

Embedded development engineers work with hardware as well as software, so some understanding of physics is required. So please, read the following article, it will give you most of the necessary information. https://alexgyver.ru/electrotech/



### Microcontroller basics

During this lesson we will be using microcontrollers to run our code.  A **microcontroller** is a compact, integrated circuit (IC) designed to perform specific tasks in embedded systems. It typically consists of:

-   A **central processing unit (CPU)** for executing instructions.
-   **Memory** (both RAM for temporary data storage and ROM/Flash for storing the program).
-   **Input/output (I/O) peripherals** for interfacing with external devices like sensors, displays, or motors.

Basically microcontroller is a computer, but completely contained inside a single **IC**, ready to be integrated into **Printed cuicuit board (PCB)** of the target device.
To simplify the process of prototyping we will be using standard PCBs. 

To make a microcontroller execute a program, the program must be flashed directly into the **ROM** of the microcrontroller with it's entrypoint at a specific memory address. This requires specific hardware (programmer) or specific software (bootloader), that is flashed on microcontroller. It is executed first and allows to process and flash new firmware to the remaining **ROM** of the microcontroller. 
We will be using second approach, so instead of flashing the chip directly, we will send the firmware via **UART** for the bootloader to flash it.

We will be working with Arduino UNO in the simulator and Digispark ATtiny85 in real world. There are a lot of useful articles to start with, I suggest you to read these, or watch some videos, I will put all these here.

- Quick start guide https://alexgyver.ru/arduino-first/
- Youtube lessons page https://alexgyver.ru/arduino_lessons/
- Digispark ATtiny85 description https://alexgyver.ru/lessons/digispark/
- ATtiny85 datasheet https://ww1.microchip.com/downloads/en/devicedoc/atmel-2586-avr-8-bit-microcontroller-attiny25-attiny45-attiny85_datasheet.pdf#G1.1910366

