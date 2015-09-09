---
layout: post
title: Creature aging
summary:
status: draft
hn-discussion:
tags:
- life_sim
---

No progress yet on the problem of getting this to run on EC2, but today I implemented creature "aging". The creature's now lose energy as a linear function to how long they have been alive. I was hopeful that this would cause populations to age more quickly as well as allow the simulation to run more quickly due to creatures dying of old age.

Step 742

![V2](/assets/life_sim_assets/v2_742.png)

Step 1820

![V2](/assets/life_sim_assets/v2_1820.png)

After this point an error caused the client to crash, although the server was still running. So for the next few images I am not sure what the actual correct ecosystem step is:

![V2](/assets/life_sim_assets/v2_4500.png)

After letting the simulation run overnight, I ended up with this:

![V2](/assets/life_sim_assets/v2_168000.png)

Clearly by implementing a lifespan the type of creature which will succeed has changed from a purely greed-based (green color seen in first simulations) one to something in between greed and fear, resulting in the browner colors.

One other note: I am seeing some strange behavior: most change seems to occur in the horizontal direction. I am not sure why this is, but it will bear further investigation.