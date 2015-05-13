---
layout: post
title: MRSD Project Progress Review 3
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
For this review period I finalized the CAD design for the brain, locomotion, and perception modules of Team D’s prototype modular robot, implemented a ROS node which allows the Udoo ARM processor to communicate with the Udoo microcontroller over serial, created a proto-board shield for a structurally secure interface between the Udoo and the motor driver of the locomotion module, and helped fabricate the 80/20 frame of the brain module.

The CAD design of the different robot modules are shown below. These designs do not include some details such as t-slot fasteners, screws, and nuts. This is primarily due to time constraints limiting the amount of time I could focus on smaller details. I would like to stress that this is the initial prototype of the robot. More time will be spent next semester on developing a robot with a better aesthetic. The purpose of this semester is to have a stable, fully functioning system that can be iterated upon.

The brain module is relatively simple, it will contain the mini-ITX computer, battery, and relevant connectors on all faces. 80/20 framing will be used as the support structure with laser-cut ¼“ acrylic used for the faceplates.

The locomotion module also uses 80/20 framing and laser cut acrylic for its mounting and support structure. It will contain motors, gearheads, wheels, casters, an Udoo, a motor driver, and a faceplate connector for mating with the brain module.

The perception module once again is made from 80/20 and laser cut acrylic. It includes an Udoo, a Kinect, and 2 Herkulex servos for panning and tilting the Kinect.

![CAD Assembly](/assets/mrsd_project_assets/prog_rev_3/cad_assembly.png)

Figure 1: CAD Assembly

![CAD Exploded View](/assets/mrsd_project_assets/prog_rev_3/cad_exploded.png)

Figure 2: Module exploded view

Implementing ROS Serial communication between the Udoo processor and Udoo microcontroller involved little changing of the microcontroller code. The only addition necessary was a ROS node subscribed to the “cmd_vel” topic, and publishing on the “velocity_reporter” topic. Both of these messages are of the Twist message type. Setting the PID targets to values based on the “cmd_vel” proved difficult, and for the sake of the demo we removed PID velocity control in favor of simple forward, backward, spin right, spin left commands.

I also fabricated a proto-board shield interface between the motor driver and the Udoo and the initial frame of the brain module. The shield can be seen in Figure 3. While not pretty, this is significantly more mechanically stable than the previous rat’s nest of wires which caused intermittent connection problems between components. The brain frame is simply cut and threaded 80/20 extrusions and corner connectors.

![UDOO with motor driver](/assets/mrsd_project_assets/prog_rev_3/udoo_motor_driver.png)

Figure 3: Udoo with proto-board shield and motor driver

![Brain Frame](/assets/mrsd_project_assets/prog_rev_3/brain_frame.png)

Figure 4: 80/20 brain module frame

After working on the ROS control and programming portions of this progress review period’s tasks, the team was anxious to get the mobile base moving. While we had not fabricated any components yet, we found some spare material in the MRSD supply room which we used as a base for the wheel and caster mounts. We used a 12V battery as the power supply and Velcro to attach the Udoo and battery to the acrylic. Once assembled, we drove the robot using a computer to publish “cmd_vel” messages which were then passed through the brain to the locomotion module’s Udoo over ethernet, then to the Udoo’s microcontroller over serial, then to the motor driver over serial. The prototype locomotion module can be seen in Figure 5.

![Prototype Locomotion Module](/assets/mrsd_project_assets/prog_rev_3/locom_module.png)

Figure 5: Prototype locomotion base w/12V battery, Udoo, motor driver, and proto-board interface shield between Udoo and motor driver

Challenges
----------
Once again, ROS integration and Udoo reliability were a constant struggle. It took a significant amount of time to get ROS Serial working on the Udoo. The system is still somewhat unreliable and the team often has to resort to restarting the Udoo, which often (but not always) returns the system to a working state. We have not yet found a way to get around these reliability problems and will likely continue to have them.

The CAD model was also a challenge as the inter-module connector design is still in a state of flux. We have all brainstormed many different kinds of connectors but have not yet agreed on any single design. At this point it is unlikely that we come up with a satisfactory connector in time for the Fall Validation Experiment and will have to resort to using screws and normal Ethernet and power connections between modules.

Teamwork
--------
Eric and I focused on the locomotion module while Mitch and Chris focused on the perception module. Eric wrote the tele-operation node, worked a great deal on ROS Serial communication, and finished the power distribution PCB with input from the rest of the team. We both fabricated the prototype locomotion base together. Mitch worked on servo control over ROS Serial and ordered parts for the team. Chris worked servo control with Mitch and began working on getting video output from the Kinect and filtering it for the line-following task of the Fall Validation Experiment.

Future Plans
------------
Before the next progress review, we plan on completing the following tasks:
Fabrication of all components
Fully assembled brain, locomotion, perception modules
Further testing of boot reliability and message passing between modules
Encoder position reporting (will be used for dead reckoning)
Full tele-operation and streaming video