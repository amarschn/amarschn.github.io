---
layout: post
title: MRSD Project Progress Review 5
summary:
status: draft
hn-discussion:
tags:
- mrsd_project
---

Individual Progress
-------------------
Since coming back from Christmas break my primary project focus has been the connection method between modules of the robot. After the second FVE the team was left without a working mobile base, as the previous mobile base had been damaged. After much internal discussion we determined that we need to rebuild the mobile base and possibly the brain and vision modules with a focus on modularity. So in focusing on modularity I have been prototyping different connection methods that will allow the user to quickly add and remove a module from the overall robot system. The stress here is on connection method rather than connector, as it is not presently certain whether we will try to stick with some kind of single point connection (i.e. a mechanically strong Ethernet connector in conjunction with some kind of power transmission connector) or separating the mechanical and electrical connection entirely.

My first task is to rebuild the mobile base in a way that allows for motor swapping. I have come up with a few concepts for connection methods that will allow for quick motor swapping, this week having modeled and printed the first concept. In Figure 1 the slide rail concept assembly can be seen.

![Slide Rail CAD](/assets/mrsd_project_assets/prog_rev_5/slide.png)

Figure 1: Slide Rail Assembly

This concept relies on slide rails and magnets for a relatively secure mechanical connection between the motor housing, and pogo pins for the electrical connection. The outer housing would be incorporated into the overall locomotion module, which could then be connected to a brain module for control.

![Slide Rail](/assets/mrsd_project_assets/prog_rev_5/slide_detail.png)

Figure 2: Slide Rail Front View

The slide rails were initially 3D-printed, but if we move forward with this design they would likely need to be lubricated or replaced with higher quality smooth material. While it appears in Figure 2 that there is a large distance (1mm) between the inner and outer rails, once 3D-printed this distance disappears due to part cooling. McMaster slide rails and rail collars made from aluminum have been identified to replace to the 3D printed slide rails and cost ~$30 per rail and collar.

![Pogo Pins](/assets/mrsd_project_assets/prog_rev_5/pogo.png)

Figure 3: Pogo Pin Contacts

![3D-Printed Slide Rail Enclosure](/assets/mrsd_project_assets/prog_rev_5/3d_print_slide.png)

Figure 4: 3D printed inner and outer housings

I have previous experience using pogo pins for electrical contact and for this connection method decided on Mill-Max pogo pin arrays. According to the Mill-Max representative Mitch and I emailed 12 pins will be good enough for Ethernet and power transmission at 12V/5A. 8 pins will be used for Ethernet, and 4 for power transmission.

Challenges
----------
We were able to get pogo pin samples shipped to us as of 1/28, however they have the wrong pin count and do not include any contact pads. This will delay testing of the pogo pins for Ethernet and power transmission.

Another challenge to the team is limited funds. Particularly in prototyping different connection methods and connectors, it is important to be able to try lots of options. However many off-the-shelf options cost a non-trivial amount of money for the budget the team has remaining. Slide rails and shaft collars from McMaster cost roughly ~$30 apiece, getting more than a few samples of pogo pins could cost up to $500, and Amphenol connectors are also in the ~$30 range. These smaller costs can add up and limit our ability to continuously prototype. We mitigate this by 3D printing what we can and focusing on the cheapest options available.

Teamwork
--------
For this semester, the team has broken out into 2 groups focused on separate aspects of the robot: Chris and Eric on improving the information architecture and inter-module communication, and Mitch and I focused on the physical and electrical connection between modules.

Chris and Eric did significant work in benchmarking the latencies of communication using different frameworks and devices over the past week, and have identified several possible options for inter-module communication. Currently the plan is to not use ROS and instead use one of the Internet of Things communication protocols.

Mitch has helped me a great deal in modeling different parts to use in the connection method prototypes, including motors and PCBs. He has also ordered parts for all team members.

Future Plans
------------
My plans for this week include prototyping a more rigid electrical interface between modules using Mill-Max pogo pins and dowel pins as guide rods, integrating a working motor module using the slide rails, and modeling a connection method using Amphenol connectors acquired from Digi-Key.

Other connection methods I plan on exploring will use off-on magnets, quarter-turn fasteners, and other slide rail orientations. It is worth noting that there will likely be several different methods of connection in the finished robot, as different module geometries necessitate different kinds of connections.

On 1/30 the team is meeting with RE2, a company which has developed their own proprietary connector for robot arms. It may be possible that they will lend us their connectors for this project, in which case my tasks will shift to integrating their connection method with our robot.