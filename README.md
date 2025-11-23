# embedded-p3-rtos-scheduler  

## Overview  
This project implements a mini real‑time operating system (RTOS) scheduler on a microcontroller (e.g., Raspberry Pi Pico or STM32). It demonstrates how to design and configure tasks, schedule them with priorities, and use message queues or semaphores for inter‑task communication. The goal is to showcase proficiency in multitasking, deterministic timing, and event‑driven design.  

The example application creates several tasks: a heartbeat LED task, a simulated sensor task that generates or reads data periodically, and a UART logging task that prints system status. The tasks communicate via a queue to decouple producers and consumers and illustrate FreeRTOS or a simple cooperative scheduler.  

## Hardware Requirements  
- Microcontroller board such as Raspberry Pi Pico (RP2040) or STM32 board.  
- On‑board LED for heartbeat.  
- USB‑UART interface for serial logging.  
- Optional: external sensor for real data (temperature, accelerometer, etc.).  

## Software Requirements  
- Pico SDK / STM32 HAL or relevant MCU SDK.  
- FreeRTOS kernel (or custom cooperative scheduler code).  
- CMake build system and Ninja.  
- GCC cross compiler for the target architecture.  

## Build & Flash Instructions  
1. Clone this repository and initialize submodules if FreeRTOS is included as a submodule.  
2. Configure the project for your target board by editing `CMakeLists.txt` and setting the correct SDK paths.  
3. Create a build directory and run `cmake ..` followed by `cmake --build .` to compile the firmware.  
4. Flash the resulting binary to your microcontroller using the appropriate tool (`picotool load -f`, `openocd`, or ST‑Link).  
5. Open a serial terminal at the configured baud rate (e.g., 115200) to view logging output.  

## Features  
- Configurable task scheduler using FreeRTOS or a simple cooperative scheduler.  
- Multiple tasks demonstrating concurrency:  
  - Heartbeat LED task toggling the LED at a constant rate.  
  - Sensor task generating or reading data at periodic intervals.  
  - UART logger task printing messages and sensor data.  
- Inter‑task communication via a queue or message buffer.  
- Clear separation of application logic and scheduler configuration.  
- Ready‑to‑use CMake build system.  

## Demo  
1. Build and flash the firmware onto the microcontroller.  
2. Open the serial terminal to observe the heartbeat messages and sensor data printed by the logger task.  
3. Adjust task priorities or periods in the code and rebuild to observe scheduling behaviour (e.g., missed deadlines or jitter).  
4. Optional: connect a real sensor and modify the sensor task to read actual data.  

## Future Work  
- Add more sophisticated tasks (e.g., command interpreter, periodic data transmission).  
- Experiment with other inter‑task communication primitives such as semaphores, mutexes, and event groups.  
- Implement dynamic memory allocation and task creation at runtime.  
- Integrate power management by suspending tasks when idle.
