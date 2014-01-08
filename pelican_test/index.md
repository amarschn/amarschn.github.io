Title: StarBlock Blog
Date: 01/05/2014
Category: StarBlock
Tags: libgdx 
Slug: star-block
Author: Drew
Summary: I talk about the development of my first libGDX game


01/01/2014 Day 1: Hello World!
------------------------------
Hello, my name is Drew, and I am developing a game, tentatively named Star Block.

Star Block will be a 2D space-shooter/spaceship-building game. Kind of like a mix between Asteroids and a 2D version of Minecraft. 

The main purpose of this blog will be to act as a development journal, something that will help motivate me when the game inevitably loses it's new project luster, and allow me to look back at my thought processes during development. I also have never set up a blog or website before, so I thought this would be a way to learn about web development. As of right now I am using Github Pages and have not yet gotten a domain name.

A bit about the game so far:

I am using the multi-platform, open source framework <a href="http://libgdx.badlogicgames.com/">LibGDX</a> which I chose largely due to it's large user base, active development, use of Java (I like Java), and because I was tired of constantly jumping from framework to framework wondering which the "best" was.

The game is focused around the idea of making 2D spaceships out of different types of squares, and using that ship to battle enemy spaceships. Right now the types of squares with which the player can build their ship are:

	1. Command Squares: the heart of the ship, lose this and your ship is toast
	2. Energy Squares: these squares power the engines and weapons of the ship
	3. Engine Squares: allow the ship to move
	4. Weapon Squares: cannons, missiles, lasers
	5. Storage Squares: store ammunition and fuel

What I like about this mechanic is that it forces the player to consider the design of their ship with their playing style, and immediately offers a kind of balance between size, speed, manueverability, durability, and firepower. Another cool aspect of this is that the functionality of your ship will change as you fight, for instance when an energy square on your ship is destroyed, all of the weapons and engines that energy square may have powered will become dead weight.

I plan on posting once a day about my development progress. I have set myself a 60 day goal of having a completed PC game. In my case completed means the following:

	-Ship construction and modification
	-Movement and combat using the previously mentioned "powered squares" game mechanics</li>
	-At least 1 playable mission
	-PC only

These are admittedly pretty modest goals, but I have never developed a full game before and I don't think it is a good idea to set unattainable milestones. With that being said, I do plan on making this game cross platform, with the next target (after PC) being Android. For now though, I will focus on the PC as my sole platform.


01/02/14 Day 2: Box2D fun
-------------------------
Today was not extremely productive unfortunately, I had planned to get Box2D going in the game, but I ran into some issues drawing the rectangle sprites for each rectangle of the user ship onto the screen so that they match the Box2D representation of the ship. For those that do not know, Box2D is an open source 2D physics engine that many games use, and, at least in my case, using Box2D means having 2 representations of any kind of object in the game, one being what the player will see (sprites), and the Box2D representation of that object, which is invisible, but which will be used to determine position, velocity, and rotation of the visible sprite. This can lead to some confusion, particularly in my case with large shapes made up of many smaller shapes. I will update this more later.

01/03/14 Day 3: Box2D not so fun
--------------------------------
I was able to get Box2D running today, so that you can make some kind of "ship" with the construction screen, and that ship will be rendered in on screen with each square of the ship set as an individual fixture part of the body of the ship. I have run into a problem however, trying to put individual sprites on each fixture of a body. The typical Box2D way seems to be mapping a single sprite to a single body. In my case, since a single ship is made up of many different blocks, I want to have a sprite for each of those blocks rather than have to create a new sprite every time the ship takes damage or otherwise changes in appearance. Not sure what to do about this one right now. I hacked a way to get the sprites attached to each fixture by making a hashmap that uses fixtures as keys and each fixture's location with respect to the body they are a part of as the value, but it doesn't feel like a clean solution. Also currently having issues with rotation, as they cause the below effects:


In other news, I have selected Pelican, a Python-based static web generator, to make this blog a little fancier. Wooooo!

01/04/14 Day 4: FAILUREEEEEEEEEEEEEEEEEE
----------------------------------------
Today was not so good. I fumbled with Box2D for an embarrassing amount of time and still am not able to get Sprites to attach correctly to fixtures within the spaceship. This is pretty frustrating, as it really is a very simple thing I am trying to do. I know there is a way, but getting there is taking a lot longer than expected. Box2D is a "pure" physics engine, meaning that it only deals in meters, Newtons, seconds, and other real-world units. When using Box2D, you create a simulated world and watch as bodies within that world interact. What this means for a game trying to use Box2D is that the game is always trying to match up what can be seen by the player with the invisible physics simulation going on in the Box2D world. I will try again tomorrow I suppose. It has been a frustrating day. 

01/05/14 Day 5: SUCCESSSSSSSSSSSSSSSSSSS
----------------------------------------
Today I was not able to get much done game-wise, however I did figure out how to correctly display the sprites onto their underlying Box2D bodies! HOORAY! The fix was, of course, pretty simple, and I didn't have to bother with storing extra location information. Although there still might end up being a performance issue, I am going to not bother with that possibility right now. 

I have got pelican working, and with a little work should have a satisfactory (for now) theme going for this blog so people (the 2 or 3 poor souls who might end up reading this) won't be completely disgusted by walls of unformatted text.

01/06/14 Day 6: Changing Sprite Colors
--------------------------------------
Slow day, but now can change sprite colors on the fly of my "ship". See the screenshots below:

Next step is to work on the making different squares of the ship act differently. I will start by making the energy squares of the ship the points at which engines exert forces. This will then necessitate a more complex control scheme, particularly for larger ships with many different energy squares with connected engine squares, as so many different points of applicable force will allow a ship to move in all kinds of different ways, and simple up, down, left, right arroy keys could not possibly control each energy square separately. What I am thinking I will use the mouse for control, by selecting points that the ship will navigate towards. Then, using the arrow keys (or WASD), the player will be able to rotate the ship or otherwise manipulate its orientation, but not affect the general movement vector, which will have been determined by the point set by the mouse. There are a few problems with this strategy, however, the main one being there will have to be a lot of background processing going on determining which energy squares of your ship are being used for rotation and which are being used for movement, and the end result could be that the player does not feel in control of their ship. I am going to have to play around with the control scheme a bit, I can already tell. One thing I am also trying to keep in mind is that I do eventually want to port this game to Android, so avoiding a great deal of keyboard control is preferable.

01/07/14 Day 7: Movement
---------------------------------------
TOday I messed with the control scheme some, but it is still not perfect. Also need to implement some kind of "ship complete" function that will not allow a player to create a ship with disconnected parts. 