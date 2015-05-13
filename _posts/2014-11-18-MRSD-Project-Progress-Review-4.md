---
layout: post
title: MRSD Project Progress Review 4
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---


Individual Progress
-------------------
For this review period I manufactured parts, did some CAD design for the perception module, helped assemble the robot modules, wrote some Arduino code for reporting encoder data, and assisted the team with many of their tasks.

My primary task was to get the robot fully assembled. This is still an ongoing task, as all of the material required for fabrication only came in today. However, we were able to get a functioning assembly in time for 11/17. Manufacturing was carried out in accordance with the design shown in Figure 1. All modules are framed with 20mm x 20mm aluminum extrusion, which needed to be cut to size and threaded to allow for inter-connections at frame joints. All faceplates were made using either 1/8” or 1/4” acrylic, laser cut to provide mounting and wiring holes. The current state of the assembly can be seen in Figure 2. The modules are all mechanically stable at this point and the team has been testing the sub-module functions. All panels have not been laser-cut yet, and all t-slot connectors have not been built into the assembly, so further work is required.


![CAD Assembly](/assets/mrsd_project_assets/prog_rev_4/cad_assembly.png)

Figure 1: CAD Assembly

![Robot Assembly](/assets/mrsd_project_assets/prog_rev_4/robot_assembly.png)

Figure 2: Front and side view of robot assembly

I also wrote the initial encoder data collection code that Eric fleshed out into a ROS-node for position commands. There are encoders on both motors of the locomotion module, with each encoder giving 360 ticks per revolution. Change in encoder state is delivered to the microcontroller on the UDOO through a polling mechanism rather than through interrupts, as this was easier to accomplish. From there the microcontroller is running a ROS node that publishes this encoder data.  From our initial testing we believe they will provide the necessary accuracy for our dead-reckoning requirements.

Challenges
----------
The primary challenges I had were time-related: getting the hardware we needed on-time and manufacturing and assembling all the modules in time for testing.

The battery, several 80/20 t-slot connectors, and acrylic faceplates took much longer than we expected to arrive, which held up the construction of the brain module. Cutting and threading 80/20 was a much larger task than I anticipated which caused delays in testing of the whole robot. At this point there are a lot of linear dependencies in testing all of the modules, so any delay in one process can cause many more delays farther down the line.

In assembling the robot the team has run into many different challenges. These include power distribution board issues, thermal issues, and module assembly time. Currently we are using power distribution boards with linear voltage regulators stepping power down from 24V to 12V for all modules. These linear regulators are bolted to small heat sinks which do not provide the thermal dissipation necessary to prevent thermal shutdown. Because of this the brain module is being powered by the bench power supply, and a fan is necessary to cool the regulator powering the perception module. The locomotion module will most likely also require a fan. The team has reacted by ordering better heatsinks, fans we can integrate into the assembly, and possible replacement voltage regulators. I would prefer to power the robot without fans where possible, although at this point I am not sure if a fan-less solution is viable.

Module assembly time could be an issue at this point, as we do not have an acceptable custom connector solution and are using off-the shelf connectors and screws to secure the different modules to each other. While this method works, it is not pretty and does not at all meet our original goal of “plug and play” functionality. The requirement for this semester is 5 minutes for assembly and boot up, which will be possible for one of us but most likely not possible for a novice user. This is not ideal and the team will have to allocate more time to come up with an acceptable connector design in the coming months.

Teamwork
--------
All team members helped with many different tasks since the last review period, including manufacturing parts, assembly, programming, and integration tasks. Mitch put together orders based on input from all team members, helped out in the cutting and threading of the many different 80/20 pieces our current design uses, and helped Chris with the line following code. Chris helped with manufacturing robot parts, wrote a lot of the line following code, and helped get all the different systems working after assembly. Eric tested the power distribution PCBs, wrote a ROS node for encoder reporting based on my initial Arduino code, helped me laser cut panels for the robot, and helped to get everything working. 

Future Plans
------------
Monday is the FVE, so all of the team’s effort will be focused on meeting the requirements we specified. At this point we are making sure all systems work together and are robust enough for demo. Chris and Mitch will be focused most heavily on the line following task, while Eric and I will focus on dead reckoning. If I have time I will try to work on a more robust and unique connector design than our current inter-module connection, which involves 4 screws, 2 Power-Pole snap connectors, and an Ethernet connector.
