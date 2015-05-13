---
layout: post
title: MRSD Project Progress Review 10
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
This progress review I performed many different tasks including designing and beginning to print cover plates for the locomotion module, laser cutting a new top cover for the locomotion module, working with Chris to re-wire the locomotion module, and designing and fabricating an ultrasound sensor module. I also attempted to laser cut a new male connector plate with dowel pins but was unsuccessful in getting the dowel pins to be straight after press-fitting them into the acrylic of the male connector.

The cover plates of the locomotion module are very slowly coming together, each piece takes between 6-8 hours to 3D print using the Makerbots. By the SVE we will have all parts complete and attached to the locomotion base. While not structurally important I think the cover will improve the robot aesthetic and make it much more attractive than last semester’s robot. Additionally, these plates have grooves built in for an LED strip which I hope to have working in time for the SVE. By screwing the plates together and then soaking them in acetone vapor the plates will become much smoother and shinier. See Figure 1 for completed cover plate pieces.

![Cover Plates](/assets/mrsd_project_assets/prog_rev_10/im1.png)

Figure 1: 3D-printed cover plates

I also laser-cut a new top plate for the locomotion module. This top plate fixes some hole discrepancies present with the old plate. I still need to cut a new bottom plate however and will do that in time for the SVE. See Figure 2 for the laser-cut top plate of the locomotion module.

![Acrylic Top](/assets/mrsd_project_assets/prog_rev_10/im2.png)

Figure 2: Laser-cut acrylic top

With Chris I helped to re-wire the locomotion module and make the Ethernet connections to the connector plates more secure using zip ties to provide some strain relief. The Ethernet connections of the connector plates particularly are tricky, as we have had to each of the 8 fragile Ethernet wires to points on a proto board. This can result in a very fragile connection prone to cold solder joints and breaking which are very difficult to debug. Hopefully with all of the Ethernet wires tightly held using zip ties there will be no wire breakage.

I also designed and fabricated a sensor module using a Raspberry Pi B+ and MaxSonar ultrasound sensor. See Figure 3 and Figure 4. This is a very simple module but will help demonstrate the modularity of the system. Mitch has worked on programming this module for the SVE.

![Sensor CAD](/assets/mrsd_project_assets/prog_rev_10/im3.png)

Figure 3: Sensor Module CAD design

![Sensor Module](/assets/mrsd_project_assets/prog_rev_10/im4.png)

Figure 4: Sensor Module assembly (with cracked front plate)

I also attempted to press-fit dowel pins into a male connection plate again, but was unsuccessful. The dowel pins ended up not being straight enough to insert properly in the dowel pin insertion points in the female connector. Fortunately the magnets and pogo pin inserts have proven somewhat sturdy without any dowel pins to lock the electrical connections in place.

Challenges
----------
Integrating the robot to be fully functioning has been very challenging. Connection issues between modules are difficult to debug, as it is not always clear whether it is a software or hardware issue. The electrical connectivity issue could be fixed with more precisely machined mating connector plates and a circuit board design for the pogo pin to Ethernet and power connection rather than just protoboard, but there is not enough time to do either of those tasks before the SVE.

In addition, both Chris and I have had difficulty getting a reliable backup of the locomotion module Odroid-C image. We are currently at a loss for why that is, but it could prove problematic if the Odroid needs to be re-flashed due to a read/write error during a boot cycle.

The 3D printers have also given the team plenty of issues when printing cover plates. The Makerbots are extremely finicky and we have had multiple prints go bad for non-obvious reasons. Fortunately we have persisted and have gotten one of the printers to print reliably. Hopefully this printer will remain in a good printing state and with more black ABS we will be able to complete all cover pieces.

Teamwork
--------
Chris worked on system integration, wiring, inter-module networking, and programming the robot controls. Mitch aided me in 3D printing the robot shell pieces, ordering parts, machining and laser cutting parts, programming the sensor module, and programming some sounds into the planned speaker system. Eric worked on the computer vision codebase.

Future Plans
------------
I will continue working with Chris to get the robot fully functioning, as well as help Mitch program the sensor module. I also hope to create a wireless control module so that we do not need an Ethernet tether for controlling the robot. The wireless module would essentially just be an Odroid with a Wi-Fi antenna, which we have on-hand, so it will not be too much of a challenge.