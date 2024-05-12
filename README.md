# Design-and-FPGA-implementation-of-PID-Controller

`ABSTRACT`
KEYWORDS: PID, Controller, FPGA, MATLAB, Simulink, DC Motor, Hardware Implementation, Real-time Speed Measurement. IR Sensor

This project presents the design of a digital Proportional-Integral-Derivative (PID) controller using MATLAB Simulink and implementation on FPGA boards.The PID controller stands out in engineering and automation systems for its adeptness in effectively regulating system behavior, making it a widely adopted control algorithm. This work focuses on developing a digital version of the PID controller, suitable for real-time applications and hardware integration.

In the design process, the PID controller is modeled using MATLAB Simulink, with a focus on optimizing key parameters like the proportional gain (Kp), integral gain (Ki),and derivative gain (Kd) to achieve the desired system response. The Simulink model is then converted into hardware description language (HDL) code compatible with FPGA platforms. The FPGA implementation of the digital PID controller offers advantages such as highspeed processing, low-latency response, and potential for parallel processing of control tasks. The controller is synthesized and mapped onto the FPGA, allowing for real-time control of physical systems or processes.

In our project, we chose the FPGA approach and employed the Xilinx Artix-7 series FPGA on the Nexys4 DDR board. We controlled the DC motor’s speed and programmed
the FPGA using Verilog HDL. Our design leveraged FPGA technology, with simulations conducted through the Xilinx Vivado tool. The real-time speed measurement was achieved
using an IR Sensor, and the L298N motor driver ensured the efficient operation of the DC motor.

`TABLE OF CONTENTS`
Candidate’s Declaration i
ACKNOWLEDGEMENTS ii
ABSTRACT iii
LIST OF TABLES vi
LIST OF FIGURES vii
ABBREVIATIONS viii
NOTATION ix
1 Introduction 1
1.1 Problem Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1
1.2 Proposed Solution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1
1.3 Overview of PID Controller . . . . . . . . . . . . . . . . . . . . . . . . 1
1.4 Literature Review . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3
1.5 PID Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4
1.5.1 Proportional Controller (P) . . . . . . . . . . . . . . . . . . . . . 5
1.5.2 Integral Controller (I) . . . . . . . . . . . . . . . . . . . . . . . . 5
1.5.3 Derivative Controller (D) . . . . . . . . . . . . . . . . . . . . . . 6
1.6 Continuous Time PID Controller . . . . . . . . . . . . . . . . . . . . . . 6
1.7 Discrete PID Controller . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
1.8 PID Tuning . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
2 Software Simulation 10
2.1 MATLAB/ SIMULINK . . . . . . . . . . . . . . . . . . . . . . . . . . 10
2.2 DC MOTOR MODELLING . . . . . . . . . . . . . . . . . . . . . . . . 10
2.3 Design of Continuous-time PID Controller in SIMULINK . . . . . . . . 12
2.4 Design of Discrete-time PID Controller in SIMULINK . . . . . . . . . . 13
2.4.1 PRACTICAL PID CONSIDERATIONS . . . . . . . . . . . . . 14
2.4.2 SIMULATION RESULTS OF DISCRETE PID CONTROLLER . 15
2.4.3 OTHER APPLICATIONS OF PID CONTROLLER . . . . . . . 16
3 Hardware 18
3.1 Introduction of Xilinx Vivado . . . . . . . . . . . . . . . . . . . . . . . . 18
3.1.1 FPGA-Based Design Flow . . . . . . . . . . . . . . . . . . . . . 18
3.2 Hardware Description Language (HDL) . . . . . . . . . . . . . . . . . . 20
3.2.1 Verilog HDL . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
3.2.2 Abstraction Levels of Verilog . . . . . . . . . . . . . . . . . . . 20
3.2.3 Features of Verilog Language . . . . . . . . . . . . . . . . . . . 21
3.3 DC Motor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21
3.4 FPGA Board . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21
3.5 L298N Motor Module . . . . . . . . . . . . . . . . . . . . . . . . . . . . 22
3.6 IR Sensor Module . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 22
3.7 PID Controller Module . . . . . . . . . . . . . . . . . . . . . . . . . . . 24
3.7.1 Proportional Block . . . . . . . . . . . . . . . . . . . . . . . . . 24
3.7.2 Integrator Block . . . . . . . . . . . . . . . . . . . . . . . . . . 24
3.7.3 Derivative Block . . . . . . . . . . . . . . . . . . . . . . . . . . 24
3.8 PWM Generation Module . . . . . . . . . . . . . . . . . . . . . . . . . . 26
3.9 Speedometer . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 27
3.9.1 Methodology . . . . . . . . . . . . . . . . . . . . . . . . . . . . 27
3.9.2 Architecture of speedometer . . . . . . . . . . . . . . . . . . . . 28
3.10 Results and Discussion . . . . . . . . . . . . . . . . . . . . . . . . . . . 28
3.11 Utilisation and Power Report . . . . . . . . . . . . . . . . . . . . . . . . 31
4 Conclusion 34
4.1 FUTURE GOALS . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35
A Verilog HDL Code for PID Controller 36
A.1 PID Module . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 36
A.1.1 ROM MODULE . . . . . . . . . . . . . . . . . . . . . . . . . . 36
A.1.2 CLOCK DIVIDER MODULE . . . . . . . . . . . . . . . . . . . 37
A.1.3 PARAMETER MODULE . . . . . . . . . . . . . . . . . . . . . 37
A.1.4 Register module . . . . . . . . . . . . . . . . . . . . . . . . . . 37
A.1.5 DT PID Module . . . . . . . . . . . . . . . . . . . . . . . . . . 38
A.1.6 Proportional Module . . . . . . . . . . . . . . . . . . . . . . . . 39
A.1.7 Integrator Module . . . . . . . . . . . . . . . . . . . . . . . . . 39
A.1.8 Derivative Module . . . . . . . . . . . . . . . . . . . . . . . . . 41
A.1.9 PWM Generation Module . . . . . . . . . . . . . . . . . . . . . 42
B Verilog HDL Code for Speed Measurement Module 43
B.1 Verilog Code for Top Module . . . . . . . . . . . . . . . . . . . . . . . . 43
B.1.1 frequency measure Module . . . . . . . . . . . . . . . . . . . . 43
B.1.2 Counter Module . . . . . . . . . . . . . . . . . . . . . . . . . . 44
B.1.3 Frequency to RPM Module . . . . . . . . . . . . . . . . . . . . . 44
B.1.4 Display Module . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
