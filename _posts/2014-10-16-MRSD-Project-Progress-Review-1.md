---
layout: post
title: MRSD Project Progress Review 1
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---


Individual Progress
-------------------
This week I worked on the gearmotor/encoder/motor driver/wheel selection for the locomotion module of our project, as well as programmed an initial ROS boot node for brain-module communication over Ethernet.

During the locomotion module component selection process I helped to create a spreadsheet based on a motor sizing document sent to us by Professor Dolan. This spreadsheet contained calculations that determined torque and RPM requirements for a robot with a given weight, wheel size, maximum speed, acceleration, and incline climbing capability. We will use 2 motors in a differential drive setup for our locomotion module. The motor sizing calculations determined a motor torque in the range of 80 oz-in to 160 oz-in and an RPM range of 190 – 380 would meet our current requirements. Several motor possibilities were found on websites such as Pololu, Robotshop, and Servocity. We eventually decided on an “all-in-one” solution from Robotshop that had 2 12V DC motors w/encoders, 1 motor driver, 2 wheels, and 2 mounting brackets. It can be found here: http://www.robotshop.com/en/drive-system-12-volt.html

In order to allow for brain-module communication we are using ROS’s built in networking messaging capabilities. A complication inherent to the modular capability of our robot is that the brain must always know what modules are connected, and where they are connected. The same connection point could potentially be used for a manipulator, a sensor, or some other kind of module. The work done this week was defining a simple process for the brain to recognize a module on a given connector and communicate with it.

Ethernet has been selected as the medium to communicate between modules, but in order to map a physical connector to an IP address, we had to use Ethernet to USB converters on the brain module. Using these adapters we are able to know which subnets are mapped to each physical connector. With this knowledge we can identify which modules are connected to which connector, and communicate with each module independently.  Chris Dunkers created a framework from which I created a boot node that would run on a module and publish “boot” messages containing its subnet. Once the brain receives a boot message with a given subnet it then publishes a boot_stop message containing that specific subnet. Once a module receives a boot_stop message containing its specific subnet, it shuts down. The RQT-Graph can be seen below in Figure 1.

![RQT-Graph](/assets/mrsd_project_assets/prog_rev_1/ros_graph.png)

Figure 1: ROS graph displaying node-to-node communication

In Figure 1, the brain node is “oddbot_boot_brain”, and the module node is “module_2”. The brain node is subscribed to the boot topic which contains boot messages from modules, which in this case are only module_2. The module node is subscribed to the boot_stop topic coming from the brain. The module node is named “module_2” because that module is on subnet 2. Its eth0 address in this example was 10.0.2.13, with the 2 being the subnet which is associated to a specific USB port on the brain module. At startup each module is dynamically named based on its current subnet using a simple bash script.

Challenges
----------
Getting the nodes to communicate was significantly more difficult than expected, primarily due to networking issues. We used the mini-ITX motherboard + i3 computer as the brain module and my laptop was used as a module. In order to properly communicate via Ethernet, both the /etc/network/hosts and /etc/network/hostnames files had to be altered on my laptop to include my user name as a host. With the help of Chris and Eric, we were able to figure out the problem and successfully demo the brain-module communication.

Teamwork
--------
I worked with Mitch Kosowski in defining the motor requirements and selecting the appropriate components. Mitch also worked with Chris Dunkers to create a component list for the perception module. Chris set up the team Github account and defined the process of git merging for the team. Chris also was vital in debugging the network issues that were causing inter-module communication problems. Eric Fuevrier-Danziger set up the network architecture and defined how each module will be identified by its subnet. He also did significant work in formulating the requirements for the power distribution board.

Future Plans
------------
By next week the team will complete the following tasks:
1. Drew/Eric: Testing the Beaglebone Black’s motor control capabilities using the onboard PRU cores. The performance of these cores will determine whether a Beaglebone or an Udoo is used for the motor control in the locomotion module.
2. Eric: Finish initial design for power distribution board.
3. Chris/Mitch: Implement message passing between rudimentary perception module and brain module
4. Drew: Implement message passing between rudimentary locomotion module and brain module
5. All: Have complete or near-complete CAD models of potential modules to be built.