---
layout: post
title: MRSD Project Progress Review 6
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
Since the last progress review I worked on the CAD design for the inter-module connection method, prototyped the electrical connection between modules, and researched different connection methods used in other modular robotic systems.

This progress review I focused on the electrical portion of the connection method, meaning a “docking port” which was based around using dowel pins as guide rods and pogo pins for the power and data transmission. Figure 1 displays the current CAD design of the assembly.

![Pogo Pins w/Dowel Pins](/assets/mrsd_project_assets/prog_rev_6/pogo_conn.png)

Figure 1: CAD Assembly of pogo connector dock

The current prototyped connector can be seen in Figure 2. This connection method offers little mechanical support, but is necessary for ensuring the pins make contact with the correct pads at the connection point. I was unable to get power or Ethernet to transmit properly in the demo, primarily due to the fact that the pads and pogo pins only had intermittent contact as the laser-cut acrylic separating the pins from the pads was slightly too thick (~2-3mm). In addition, the solder joints connecting the pogo pins to the Ethernet wiring were not as robust as I would like and may have broken.

![Pogo Pins w/Dowel Pins](/assets/mrsd_project_assets/prog_rev_6/pogo_conn_real.png)

Figure 2: Prototyped pogo connector dock

I did some research into other robotic systems in order to study other kinds of connectors and locking mechanisms, many of which are recorded in the excellent paper “Electropermanent Magnetic Connectors and Actuators: Devices and Their Application in Programmable Matter” by Ara Knaian of MIT. Overall my findings have resulted in a breakdown matrix shown in Table 1.

Table 1: Connector comparison matrix

![Comparison](/assets/mrsd_project_assets/prog_rev_6/comparison_table.png)

There are certainly many more different kinds of connections (see the aforementioned paper by Ara) that are possible but I am focusing primarily on these methods. On the 12th I am meeting with Ben Brown to discuss different possibilities, as it has become apparent I do not have the time to prototype nearly as much as I would like to determine an ideal candidate solution.

Active mechanical connections have the advantage of being very strong once locked, only requiring power to switch states from locked to unlocked and vice versa. The disadvantage is that they add bulk, complexity, and require additional code and hardware to lock and unlock.

Inactive mechanical connections are simpler to create, more intuitive, and require no additional software. However they typically put constrains on the kinds of module shapes that can work. The primary tradeoff for these kinds of connections is in ease-of-use vs. durability. Simply using screws to secure every module to the other modules would be very secure, but would be less useable for a novice user and be against the general idea of a “modular robot” (in my opinion). Using simpler plastic or metal snaps offers a very easy to operate connection, but little mechanical rigidity.

Active magnetic connection and locking mechanisms are very interesting, in that they allow for no moving parts (with the exception of mechanically-switched permanent magnets), can be very durable, and would not take up a large amount of room. The front runner for these types of connections would be the electro-permanent magnet which only requires current to switch from “on” to “off”. However I cannot find a reputable vendor these kinds of magnets, and while the materials for building one myself are relatively cheap, I do not believe I have the time to build magnets, integrate the magnets into a connector, and integrate the connector into the overall robot.
Permanent magnets are very cheap, easy to use, and take up no space or electrical power. They are used in many other modular robotic systems. However the issue is how strong to make the magnets. The strength of the magnet will determine how durable the connection is as well as how easy it is to remove the module. 

An overall advantage to “active” connections, both mechanical and electrical, is that they do not limit the geometry of the modules. As long as a module has a space where the connector can fit, then it can connect with the corresponding connector on another module with no physical interaction required by the user. Any module that must be rotated in order to lock to another module requires that there be no obstructions in the way of the full rotation or the connection cannot be made. All of the active connector ideas only require linear modular placement (the rotation and locking take place in the motors or servos rather than manually).

Despite the disadvantages of active connections, my current feeling is to move forward with a rotary “snap” connection/locking mechanism. I believe it offers the best compromise in time to completion, connection strength, cost, and manufacturability.

Challenges
----------
The primary issue since the last progress review has been time. Due to mounting assignments in other classes as well as personal commitments, it has been very difficult to find time to work on the project. 

We have also had part delays in getting the pogo pins, and some fabrication issues using the laser cutter. 

Teamwork
--------
Eric and Chris both worked on the software of getting the motor to work using REST, as well as deciding to switch to ROS for future work. Chris specifically worked on PID control and Eric worked on the REST communication framework. Mitch did CAD work as well as helped fabricate the pogo pin electrical connector.

Future Plans
------------
For the next review period, we plan on having integrated motor modules working through ROS. This means a full-fledged connection method and housing for the motor modules, a functioning mobile base, and the code to make all of the modules function together.

My focus will remain on designing and building a functioning inter-module connector that will satisfy as many of our requirements as possible.