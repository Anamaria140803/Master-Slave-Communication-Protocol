# Master-Slave Communication Protocol (RS-485)

A serial communication project written in C for a network of 3 microcontrollers communicating over a shared RS-485 bus.

## Hardware & Tools
* **Microcontroller:** Silicon Labs C8051F040 (BIG8051 board)
* **IDE & Compiler:** Keil PK51 (C51)
* **Communication:** UART (RS-485 transceiver), 115200 baud

## How It Works
* **Dynamic Master-Slave:** Nodes start as slaves. If the bus is silent, a node times out and automatically takes over as master to poll the others.
* **9-bit UART Mode:** The 9th bit distinguishes address bytes from data, allowing microcontrollers to filter messages directly in hardware.
* **Non-blocking FSM:** Uses state machines for both bus communication and the user interface so the system stays responsive.
* **Error Handling:** Includes LRC checksum verification and checks bus echo after transmission to detect collisions.

## Key Files
* `MS-JT.c` - Main program loop and system initialization
* `TxMesajV4.c` / `RxMesajV4.c` - Message sending, receiving, and validation
* `UserIO.c` - Terminal and LCD interface handling
* `Protocol.h` - Message structures and communication parameters
