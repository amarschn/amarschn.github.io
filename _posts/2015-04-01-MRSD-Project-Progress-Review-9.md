---
layout: post
title: MRSD Project Progress Review 9
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
Since the last progress review most of my time has been spent finishing the design of the locomotion module, fabricating the necessary components, and assembling it. The design of the locomotion module was primarily completed as of last progress review, with only slight tweaks of component placement in the main design. I did spend some time however thinking about and designing an auxiliary method for securing modules to the top plate connector of the locomotion module.

This top plate is completely open, and so any module attached to it does not benefit from being locked into place by side walls like the other module ports. To help lock in potential modules that would be placed on the top of the locomotion module I designed a servo-driven rack and pinion locking mechanism. Two of these mechanisms can be screwed into place inside of the locomotion module on either side of the top connector plate. The design of this mechanism can be seen in Figure 1. In order to properly lock in an external module, the external module will require locking tabs to slide into the corresponding tab holes of the locomotion module top plate, shown in Figure 2.

The pinion gear will be servo-driven, with commands sent to the servo based on communication from the Odroid which will in turn be informed of a module connection through Ethernet (once a module is attached to the top plate, it will receive power through the pogo pins and should communicate it’s relevant information over the Ethernet pogo pins, which the Odroid can then use to trigger the servo). Up to 4 limit switches can be used to verify the ‘racks’ are in the correct position (locked or unlocked). These limit switches will also be wired to the Odroid. I have laser-cut an initial version of this rack and pinion mechanism but have not had time to fully assemble and test it.

![Locomotion Profile](/assets/mrsd_project_assets/prog_rev_9/im1.png)

Figure 1: Rack and pinion locking mechanism

![Locomotion Profile](/assets/mrsd_project_assets/prog_rev_9/im2.png)

Figure 2: Rack and pinion locking mechanism location on locomotion module

After finishing the locomotion module design I focused on fabricating all necessary components. The locomotion module is similar in design constraints to the motor module in that I wanted to stick with laser-cut acrylic and aluminum extrusion (disregarding the 3D printed outer shell, which is only necessary for aesthetic purposes and has not yet been created). After fabricating, I assembled the locomotion module with my team and tested basic connector functionality. The assembled locomotion module can be seen in Figure 3. I have also tested 3D printing a portion of the cover using the Makerbots, which was somewhat successful although difficult to clean up. We hope to use acetone or other methods to further improve the finish of cover pieces in the future.

![Locomotion Profile](/assets/mrsd_project_assets/prog_rev_9/locom_base.png)

Figure 3: Assembled locomotion module

Challenges
----------
We had several challenges over the last 2 weeks in building and programming the locomotion module. To laser-cut the large top and bottom panels required a laser cutter with a build volume of at least 2’ x 2’. The RI machine shop laser cutter is both too small and currently out of commission, with no clear date when it will be operational. The ChemE machine shop has a large laser cutter, but I discovered this laser cutter is also broken with no given date when it will be fixed. So I decided to cut both the top and bottom acrylic cover pieces in half and then use screws and threaded aluminum plates to bring the halves together. I used the ME machine shop laser cutters for all laser cutting work.

Another problem that occurred during the build process was improperly inserted dowel pins. For all male module connections I have designed in holes to which dowel pins will be press-fit. However I cut the holes too wide in delrin I am using for male connectors, and as a result the dowel pins were too loose or only went in at an improper angle that prevented mating with a female connector. So we removed the dowel pins for demo purposes. So far having no dowel pins has had no ill effects on the connection, the magnets hold very well and the electrical connection between pogo pins is solid.

After constructing the locomotion module we had difficulties getting any ROS code to compile on the ODroid-C1, which is the main processor onboard the locomotion module. This problem has yet to be fully solved and Chris is focusing on it. There were also a variety of networking issues in which different modules won’t communicate properly due to dynamic IP addressing.

Teamwork
--------
Since last progress review we have focused on building the locomotion module and programming it. Chris, Eric, and Mitch all helped to fabricate and assemble all parts of the locomotion module. Chris worked on programming the locomotion module and Eric worked on further developing the robot localization and tracking portion of the project. Mitch worked on developing a sensor module to be plugged into the locomotion module front and back ports.

Future Plans
------------
Mitch will focus on further developing sensor modules that fit the form factor necessary to plug into the locomotion module front and back module ports. Chris will work on the trajectory planner and debugging issues relating to locomotion control. Eric is focusing on developing the localization and tracking algorithms using external cameras. I will work on building a module which can be attached to the locomotion module top-port that will have a camera and i3 brain module for tele-operation and line following, as well as improve the existing locomotion module with 3D printed covers.