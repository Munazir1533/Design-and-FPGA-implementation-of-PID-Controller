# Design and FPGA Implementation of PID Controller

## ABSTRACT

**KEYWORDS:** PID, Controller, FPGA, MATLAB, Simulink, DC Motor, Hardware Implementation, Real-time Speed Measurement, IR Sensor.

This project presents the design and FPGA implementation of a digital Proportional-Integral-Derivative (PID) controller using MATLAB Simulink. The PID controller is widely adopted in engineering and automation systems for its adeptness in effectively regulating system behavior. The focus of this work is on developing a digital version of the PID controller suitable for real-time applications and hardware integration.

The design process involves modeling the PID controller in MATLAB Simulink and optimizing key parameters such as proportional gain (Kp), integral gain (Ki), and derivative gain (Kd) to achieve the desired system response. The Simulink model is then converted into hardware description language (HDL) code compatible with FPGA platforms. The FPGA implementation offers advantages such as high-speed processing, low-latency response, and potential for parallel processing of control tasks. The controller is synthesized and mapped onto the FPGA, enabling real-time control of physical systems or processes.

In this project, we chose the FPGA approach and utilized the Xilinx Artix-7 series FPGA on the Nexys4 DDR board. We controlled the speed of a DC motor and programmed the FPGA using Verilog HDL. Our design leveraged FPGA technology, with simulations conducted through the Xilinx Vivado tool. Real-time speed measurement was achieved using an IR Sensor, and the L298N motor driver ensured efficient operation of the DC motor.

## TABLE OF CONTENTS

1. Candidate’s Declaration
2. ACKNOWLEDGEMENTS
3. ABSTRACT
4. LIST OF TABLES
5. LIST OF FIGURES
6. ABBREVIATIONS
7. NOTATION
8. Introduction
   - Problem Statement
   - Proposed Solution
   - Overview of PID Controller
   - Literature Review
   - PID Algorithm
     - Proportional Controller (P)
     - Integral Controller (I)
     - Derivative Controller (D)
   - Continuous Time PID Controller
   - Discrete PID Controller
   - PID Tuning
9. Software Simulation
   - MATLAB/Simulink
   - DC Motor Modelling
   - Design of Continuous-time PID Controller in Simulink
   - Design of Discrete-time PID Controller in Simulink
   - Practical PID Considerations
   - Simulation Results of Discrete PID Controller
   - Other Applications of PID Controller
10. Hardware
    - Introduction of Xilinx Vivado
    - Hardware Description Language (HDL)
      - Verilog HDL
      - Abstraction Levels of Verilog
      - Features of Verilog Language
    - DC Motor
    - FPGA Board
    - L298N Motor Module
    - IR Sensor Module
    - PID Controller Module
      - Proportional Block
      - Integrator Block
      - Derivative Block
    - PWM Generation Module
    - Speedometer
      - Methodology
      - Architecture of Speedometer
    - Results and Discussion
    - Utilisation and Power Report
11. Conclusion
    - Future Goals
12. Verilog HDL Code for PID Controller
    - PID Module
      - ROM Module
      - Clock Divider Module
      - Parameter Module
      - Register Module
      - DT PID Module
      - Proportional Module
      - Integrator Module
      - Derivative Module
      - PWM Generation Module
13. Verilog HDL Code for Speed Measurement Module
    - Verilog Code for Top Module
      - Frequency Measure Module
      - Counter Module
      - Frequency to RPM Module
      - Display Module

![project_output](https://github.com/Munazir1533/Design-and-FPGA-implementation-of-PID-Controller/assets/93303360/78d8a4ac-a6d4-4eca-8677-78c0eaf0e865)

