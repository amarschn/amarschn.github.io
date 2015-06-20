---
layout: post
title: Implementation?
summary:
status: draft
hn-discussion:
tags:
- life_sim
---

How the heck do I implement all of this? I think I am going to go a little crazy and try multiple new technologies at once. This might be a horrible idea, but oh well. So the plan is to use Julia, Docker, WebSockets, and Amazon EC2.

My current thoughts (and understanding) are that I can run a Docker container on an EC2 instance, the docker container will have the backend Julia code running the ecosystem simulation. This backend will then communicate through WebSockets some kind of information (json?) which will be displayed by a browser. Makes sense? Sort of?


