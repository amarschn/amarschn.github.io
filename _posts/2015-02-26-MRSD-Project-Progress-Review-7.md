---
layout: post
title: MRSD Project Progress Review 7
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
At the end of the last progress review I had determined that the appropriate connector for the modular robot and specifically for the motor module was a twisting lock connection method. Figure 1 displays one concept of such a connector in male and female forms. The male side has pogo pins which will transmit electrical power and information between modules, dowel pins as guide rods for pogo pin contact, and outer dowel “hooks” which would act to keep the module secure once rotated into place. The movement into a locked position can be seen in Figure 2 and Figure 3.

![Star Connector](/assets/mrsd_project_assets/prog_rev_7/star_conn_1.png)

Figure 1: "Star" pattern twist lock connector concept

![Star Connector](/assets/mrsd_project_assets/prog_rev_7/star_conn_2.png)

Figure 2: "Star" pattern twist lock connector in mid-mate procedure

![Star Connector](/assets/mrsd_project_assets/prog_rev_7/star_conn_3.png)

Figure 3: "Star" concept twist lock connector engaged.

This method requires some form of rotation of the actual pogo pins however, and so a bearing would be necessary on the female side to allow rotation. Another complication of this method of locking is that it would require some form of spring mechanism on each of the “hooks” that would catch once the twist lock connector had fully engaged. Machining upward curving shelves around each “hook” slot would also likely be necessary in order to ensure a firm pogo pin connection. These tasks would mandate significant fabrication time.

On February 13th I had a discussion with Ben Brown about different connection methods. He had some experience with magnets, and agreed with my assertion that they would be the quickest method to prototype and build. So I moved forward with a concept for magnetic inter-module connectors.

In my initial designs I assumed that the magnets could be press-fit into acrylic or glued into place. However once I received the magnets (from magnets4less, an excellent and cheap magnet vendor), it became apparent that they were liable to cracking given rough treatment. With that in mind I re-designed the connectors to have “magnet containment vessels”, which in this case were simple 3D-printed containers and lids for the magnets. This way I could avoid press fitting the magnets or risking magnet damage. The disadvantage is that the magnet attraction strength is lessened by the thickness of the vessel walls. I am still working on what will be a thin enough wall for a strong yet detachable attraction force. In Figure 4 it is visible that I only used 2 magnets and requisite containers per connector. This was due to volume interference with the aluminum extrusion used as support in the final motor module. I plan on re-designing the magnet placement pattern to avoid any interference with the aluminum supports.

![Magnetic Connector](/assets/mrsd_project_assets/prog_rev_7/mag_conn.png)

Figure 4: Magnetic connector assembly using only 2 magnets

![Motor Module](/assets/mrsd_project_assets/prog_rev_7/motor_module_cad.png)

Figure 5: Model of complete motor module assembly

Figure 5 displays the competed motor module assembly design. This module will be plugged into the (yet-to-be-built) locomotion module and will be interchangeable with other motor modules. It contains a BeagleBone Black, a motor driver, motor, and 12/5V voltage converter for the BeagleBone. Figure 6 shows a fully assembled motor module. Female-Male connector tests were successful, and the magnets were strong enough to make the female plate secure but not extremely difficult for a human operator to detach. 

![Motor Module](/assets/mrsd_project_assets/prog_rev_7/motor_module_real.png)

Figure 6: Fabricated and assembled motor module


In my discussion with Ben Brown, it became clear that there is no good connection method for modules that range significantly in size and weight and so I will be exploring other connection methods for larger modules such as the brain or perception modules. For now though, this module form factor works well with magnets and can be modified to contain sensors, different kinds of motors and wheels, and even potentially batteries or more powerful computers.

Challenges
----------
Once again the main challenge was getting everything done in time. Ordered parts did not come in until the week of the progress review and the RI machine shop laser cutter was broken over the weekend, so fabrication by necessity was last minute. The team did a very good job of executing at the end however and were able to get the motor module working.

Looking forward, timing will remain an issue as well as budget. The team is officially on the last $1000 and so we have to be sparing with what we spend our money on. Because I am doing the bulk of the mechanical work and we are building many modules, I am going to be spending the majority of the remaining money on new materials and hardware in order to build new modules. This will mean relying less on McMaster, which is high-quality and fast delivery at large expense, and finding cheaper part and material vendors.

A continuous challenge will be determining appropriate connector design for different modules. As mentioned earlier, there is no perfect connector, and only using magnets for securing a heavy module (such as the brain, which weighs ~20lbs) is not ideal. Moving forward however we will have to make decisions about what the maximum size and weight modules we can use are.

Teamwork
--------
Eric and Chris both worked on getting PID motor control working using the BeagleBone Black and ROS. This involved modifying the device drivers of the BeagleBone in order to get the correct version of ROS and the eQEP modules working together. Mitch helped me design all of the components of the motor module in Solidworks, ordered components, and helped me fabricate them in the RI machine shop. All team members aided in assembling and wiring the motor modules.

Future Plans
------------
We plan on having an operational locomotion module and 2 motor modules as well as a robot trajectory planning implementation done by the next progress review. Mitch and I will focus on the mechanical design and fabrication of all of the necessary parts, and Chris and Eric will focus on the trajectory planning algorithm.