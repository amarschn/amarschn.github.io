---
layout: post
title: Testing different aging costs
summary:
status: draft
hn-discussion:
tags:
- life_sim
---

I tried playing with multiple different aging costs. Here is a relatively stable ecosystem at no aging cost:

![V1](/assets/life_sim_assets/v1_120000.png)

Here is a stable ecosystem with a linear aging cost whereby energy is removed from a creature per round directly proportional to how long the creature has been alive:

![V2](/assets/life_sim_assets/v2_168000.png)

And here is a stable ecosystem where the aging cost is still linear but an order of magnitude larger than the previous ecosystem:

![V3](/assets/life_sim_assets/v3_14000.png)

Clearly there is a trend here where as average lifetime decreases, creatures with a higher fear and social aspect (lending the purple color) start to dominate. So in order to encourage more diversity I added in an evolvable creature metabolism value. This value is summed with the creature's base metabolism to create the energy that is removed from the creature per round. In other words, creatures can "evolve" their own lifespans. After letting a simulation run overnight I returned to this diverse ecosystem:

![V4](/assets/life_sim_assets/v4_82000.png)

This is a spectacular result, with many completely different species evolving simultaneously with no species or general trait completely dominant. The primary colors are clearly green and purple, which indicates a mix of long-lived (green) and short-lived (purple) organisms.