---
layout: post
title: MRSD Project Progress Review 8
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
In this progress review period I focused on completing the design for the locomotion module as well as helping to construct a very rough platform for Chris and Eric to test their software on the motor modules we have constructed.

In designing the locomotion base I wanted there to be multiple spots for module connections, a low center of gravity, battery power (rather than last semester, where the battery was located within the brain module which sat on top of the locomotion module), and a more secure method of attaching a brain module.

First I focused on creating a general profile for the locomotion base (See Error: Reference source not found). I wanted to be able to fit 4 modules of the motor module form factor into the locomotion base, and this determined the general shape. I positioned the module locations within the locomotion base such that 2 locations would be most ideal for motor modules, and 2 locations would be ideal for sensor modules. To keep the base stable I added space for 2 caster wheels. I considered other shapes, but settled on this one because it offered the best stability, could be mobile with only 2 motor modules, and allows for mobility using traditional wheels or omni-wheels (other designs I considered were more symmetric in design, but would either require more motor modules for control or would have less logical sensor module locations).

![Locomotion Profile](/assets/mrsd_project_assets/prog_rev_8/im1.png)

Figure 1: Locomotion Base Top-Down Profile

Next I created a wiring schematic for the robot to determine all needed electrical parts (see Figure 2) and to verify that all modules could be powered by the battery and voltage converter. All modules will be powered/communicate using the same pinout shown in Figure 3 and Figure 4. This pinout has all 8 pins of Ethernet as well as 4 pins for power and 4 for ground. I am using Mill-Max pogo pins which according to a Mill-Max supplier should be able to comfortably provide up to 2 amps per pin. This means a maximum power draw of 8 amps per module at 12V, which is well within our calculated power ranges for the motors and processors we are using. The voltage convert we have only supports up to 20 amps, which is why there are mounting positions for 2 voltage converters.

![Locomotion Wiring Diagram](/assets/mrsd_project_assets/prog_rev_8/im2.png)

Figure 2: Locomotion Module Wiring Diagram

![Female Pinout](/assets/mrsd_project_assets/prog_rev_8/im3.png)

Figure 3: Female Pinout for power/data

![Male Pinout](/assets/mrsd_project_assets/prog_rev_8/im4.png)

Figure 4: Male Pinout for power/data

Finally, I added mounting holes, support framing, and support walls to the CAD design to better contain each motor or sensor module within the locomotion module. The locomotion module will primarily consist of laser-cut acrylic and aluminum extrusion framing, with a 3D printed outer shell.

![Locomotion Module CAD](/assets/mrsd_project_assets/prog_rev_8/im5.png)

Figure 5: Locomotion Base w/Motor Modules

Challenges
----------
We had planned on having more of the locomotion module built by the time of this progress review, but I was unable to complete the mechanical design in time. Ordering times for some materials, such as acrylic which we are sourcing from a cheap non-McMaster source also took more time than expected to arrive.

We have also had trouble accurately controlling the robot position, but this is most likely due to the fact that we used ropes to secure the motor modules to the prototype locomotion base. Our current hope is that the system will be significantly more precise once the motor modules are securely locked into place.

Teamwork
--------
I focused primarily on designing the locomotion base with Mitch assisting me in CAD modeling and ordering parts. Chris and Eric wrote the trajectory planning and control ROS nodes to control the motor modules. These nodes were broken out into a global and local planner. The global planner creates a desired path and the local planner sends command velocities to the individual motor modules to stay on the desired path. We all helped to finish constructing and re-wiring the motor modules and the wiring on the prototype locomotion base.

Future Plans
------------
There are still a few parts to design, including brackets for the ODroid, the power switch, and other components. We also plan on adding an individually addressable LED strip to the outside of the locomotion base to allow for better robot tracking when the locomotion base is being tracked by an external camera.

The design shown in this document is almost entirely complete, and so the next step is to begin building. Mitch and I have been compiling a BOM and plan on finalizing all of our orders by 3/20, and having the entire locomotion base built by 3/27. Chris and Eric will help in the fabrication as well as begin work on the computer vision and trajectory planning software of the robot.
