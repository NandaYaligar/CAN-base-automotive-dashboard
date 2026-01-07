# CAN-base-automotive-dashboard
CAN based Automotive dashboard: Designed and implemented a CAN communication system using 3 ECUs (PIC microcontrollers).

ECU 1:
* Measured engine speed using a potentiometer (10-bit ADC mapped from 0–1023 to 0–100).
* Monitored engine temperature.
* Implemented gear position control using a matrix keypad
Key 1 → Gear increment
Key 2 → Gear decrement
Key 3 → Collision indication.
* Transmitted each parameter to ECU 3 using separate CAN message IDs.
  
ECU 2:
* Measured engine RPM / temperature range (18–27°C) using ADC and scaling logic.
* Implemented indicator status input using a digital keypad.
*Sent each signal independently to ECU 3 with unique CAN IDs.

ECU 3:
* Acted as a CAN receiver node.
* Collected data from ECU 1 and ECU 2.
* Displayed all received vehicle parameters on a CLCD.

Why I Built It:
* To understand real-time CAN protocol communication used in automotive ECUs.
* To gain hands-on experience with:
* Multi-node CAN networks
* Sensor data acquisition
* Message ID–based data segregation
* To simulate vehicle dashboard behavior, where multiple ECUs communicate with a central display unit.
  
What I Personally Worked On
* Configured CAN peripheral initialization (bit timing, baud rate, filters) using the PIC datasheet.
* Implemented ADC configuration and scaling calculations for engine speed and temperature.
* Designed CAN message framing with separate identifiers for each parameter.
* Developed keypad interfacing logic for gear control, collision input, and indicators.
* Implemented CAN transmit and receive routines across all ECUs.
* Integrated CLCD driver and formatted live data display in ECU 3.
* Debugged communication using message ID tracing and data validation.
  
What Broke or Failed
* Initially faced CAN message collisions and data mismatch due to incorrect message ID configuration.
* ADC values showed incorrect readings due to improper scaling and reference voltage assumptions.
* CLCD display flickering occurred because of improper CAN receive synchronization.
* Keypad debouncing issues caused false gear changes. Fixes applied:
* Corrected CAN ID mapping and receive filters.
* Recalculated ADC scaling logic.
* Optimized CAN receive handling and display refresh timing.
* Added software debouncing for key inputs

What I Learned
* Practical understanding of CAN protocol architecture and multi-ECU communication.
* How message IDs control data flow in automotive networks.
* Importance of ADC resolution, scaling, and calibration in sensor interfacing.
Real-time debugging techniques in embedded systems.
How multiple peripherals (ADC, CAN, keypad, CLCD) interact in a single firmware system.
Writing robust, modular embedded C code aligned with automotive use cases.
