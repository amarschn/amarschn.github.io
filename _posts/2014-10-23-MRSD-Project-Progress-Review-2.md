---
layout: post
title: MRSD Project Progress Review 2
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---


Individual Progress
-------------------
This week I chose between using a Beaglebone Black (BBB) or an Udoo for the locomotion module computing platform, implemented PID motor control using the Udoo and a laptop for user commands, and did significant portions of the initial prototype CAD designs of the different robot modules.

Deciding between the BBB and the Udoo turned out to be more challenging than anticipated. My first reaction was to use the BBB, as it has a larger user base, more online documentation, lower power requirements, smaller form factor, and (in my opinion) a much cleaner and more attractive layout. I wanted to utilize the 200MHz Programmable Real-time Units (PRUs) on the BBB. The PRUs can trigger and receive interrupts, read ADC values, access main memory, and allow for very tight control loops for things like motors. However, once I attempted to actually use the PRUs I ran into several problems which I was unable to solve. Strange make-file errors, poor or nonexistent documentation online, and recommendations from several people led me to drop the BBB as the main candidate for the computing platform on the locomotion module and use the Udoo Quad instead.

The Udoo has an Atmel SAM3X8E microcontroller (the same as the Arduino Due), as well as quad-core ARM chip capable of running ROS. With some help from Eric who had already worked with the Udoo, we were able to get the Arduino development environment set up quickly and relatively painlessly. Eric also helped to design and 3D print a mounting fixture for the motors and motor driver in order to allow for safe testing of motor speed control. At this stage actual work in controlling the motors could commence.

Last week we received the motor kit we ordered from Robotshop, which included DC motors, encoders, wheels, and a motor driver. It requires 12V to power the motors, includes suppression capacitors, and is capable of either serial communication using a 5V TTL bus or I2C communication based on different jumper configurations on the board. I decided to use serial commands rather than I2C, primarily because of their simplicity and my familiarity with controlling and communicating with motors over serial. After connecting the RX/TX pins of the motor driver to the TX1/RX1 pins of the Atmel chip on the Udoo, I was able to get serial communication running between the Udoo and the motor driver very quickly. 


![Motor Driver Pinout](/assets/mrsd_project_assets/prog_rev_2/motor_driver_pinout.png)
Figure 1: Motor Driver Pinout

After serial communication between the Udoo and motor driver was established and stable, I implemented PID velocity control using the “PID_v1” Arduino library (can be found in appendix). The library is robust and easy to implement on an Arduino, requiring an initial setting of parameters for the gains, and a variable address for the input, output, and setpoint of the controller. In this case, the input of the controller was the velocity reading of the motors. This reading was provided by sending the serial instruction “0x21” to the motor driver board and reading the corresponding serial output (in the range of 0-255). Currently the user sets the desired speed or setpoint manually through the Arduino IDE’s serial monitor or through another method of serial communication. The output value of the PID controller is determined using the “Compute()” function of the PID_v1 library, which is running constantly in the main loop. This output value is in the range of 0-255 (similar to the input) and is then sent as an argument of the instruction “0x31” back to the motor driver, which then regulates the speed of the motors. Hand-tuning the gains took longer than expected and will likely continue into the future, but as of now the performance can be seen in Figure 2.

![PID Graph](/assets/mrsd_project_assets/prog_rev_2/pid_graph.png)
Figure 2: PID Performance

The values seen in the y-axis of Figure 2 are the “speeds” as communicated by the motor driver over serial. They range from 0-255 with a return value of 128 indicating the motors are at rest. A value of 0 indicates the motors are driving at full power backward, and a value of 255 indicates the motors are driving at full power forward. The graph shown in Figure 2 displays the results of a quick performance test over a period of ~30 seconds where the motors were initially at rest, given a command to go backward at full power, and then given a command to go forward at full power.

Challenges
----------
The most difficult aspects of this progress review were primarily getting a functioning setup. Attempting to compile, debug, and research example code for the BBB PRU’s took a large portion of time which would have been better spent getting the Udoo up and running. The Udoo, while simpler to setup than the BBB, required the newest version of the Arduino IDE and occasionally would need resetting for no obvious reason.

Teamwork
--------
I worked with Eric on getting the Udoo development environment up and running, as well as helped him design a mounting fixture for the motors and motor driver. I also helped Mitch become more familiar with ROS while he programmed the initial sensor module messaging node. Chris was gone for the long weekend visiting his family but was able to contribute significantly by taking responsibility for all merging to the team git repository as well as program and test the Udoo’s ROS vision capabilities.

Future Plans
------------
Currently the primary goal of the team is to get a full bench prototype up and running. This means that all ROS nodes are communicating actual data, serial commands are coming to the Atmel chip on the Udoo through the ARM processor on the Udoo rather than directly through the user, and all modules are capable of being powered by battery. We also will have completely finalized CAD designs soon for the initial brain and locomotion modules, which I will have primary responsibility in fabricating. Mitch and Chris will work on the vision module subsystem, while Eric and I focus on the locomotion module subsystem.

Appendix
--------
1. Motor Kit: http://www.robotshop.com/en/drive-system-12-volt.html
2. Motor Driver: http://www.robotshop.com/media/files/pdf/md25-documentation-md25.pdf
3. Motor Driver Serial Commands: http://www.robotshop.com/media/files/pdf/md25_serial_documentation.pdf
4. Arduino PID Library: http://playground.arduino.cc/Code/PIDLibrary