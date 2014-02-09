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

01/08/14 Day 8: 
---------------
Didn't feel too great, and had some other business to take care of.

01/09/14 Day 9:
---------------
School apps, no progress.

01/10/14 Day 10: I opened Eclipse today! Gold star!
---------------------------------------------------
Well, my 60-day deadline 1/6 over already. Do I feel like I am on track? Not a chance. There is still so much to do. Today I worked some and was able to implement movement applied to individual squares in your ship, but it is not yet incorporated into the ship so that the energy squares are the points of force application. Overall, I am dissapointed with my current progress, and my blog posts obviously reflect that, as they are all short with little to report. I'm not going to stop though, and this weekend I plan on getting a lot done, hopefully I won't waste a ton of hours messing with Box2D this time around.

Since this is day 10, I am going to arbitrarily have an overview of what I still have planned, in no particular order, here goes:
1. Implement fully functioning ship, with keyboard + mouse control scheme
2. Implement enemy ships, with some kind of AI/pathing/fighting capabilities
3. Create destructible asteroids
4. Make a not-terrible splash screen and mission selection screen
5. Create artwork for game (more block types, and maybe a logo)

So that is a very broad view of things I have to do, each of them is going to take some time and subdivision into smaller tasks. Right now my focus is just on getting the user the capability to build a ship and then fly it around. After that I will probably try to create some enemy types to play with and verify basic game playability.

01/11/14 Day 11: Some progress
------------------------------
Today I was able to get the player's ship to start moving more like how I envisioned it. I am not sure if I have fully illuminated how I want my ship to move, so I'll give some more detail now. Alright, first imagine the ship as a some cluster of squares, each square of some kind of type, this case lets just assume the only available types are:

- A square that powers the squares to its top, bottom, left, and right
- A square that exerts a force on the square that powers it, in only one direction

Using a combination of of these two kinds of squares, we can make a very basic ship, as shown in the below screenshot:

(SHOW SCREENSHOT)

In this ship, the yellow (it is a faded yellow so it is kind of hard to make out, but it is the center square) is the first kind of square. It powers the squares adjacent to it (the green and gray squares), and is the one square in which force is applied. 

The other four squares are all of the second type, that which are powered by the center square and so can exert force on it. The green and gray squares both refer to the second type of square mentioned, with green representing squares that are currently exerting force, and gray being squares that are not exerting force. The other thing to consider is this second type of square, the one that exerts force on the middle square, can only exert force in one direction, that direction being towards the powering square. So, with this sample ship, the square at the top can push down on the center square, thus pushing the whole ship downward, the square at the right can push leftwards on the center square, thus pushing the entire ship leftward, and so on. With this simple ship, we have all 4 directions of the compass covered, and the ship can move any which way it wants.

Now let's get a little more complicated.

What if there are more than one of the first type of square, the type that powers the ship? And different numbers of the second type of square stacked up on top of each other? What happens? What if it looks like this:

(SHOW SCREENSHOT)

Well, what happens is it gets tough to control. You have these multiple points of force acting on the ship, and what typically occurs is you spin out of control and have no idea what is going on. Not too fun. So, to counteract this, we need some smarts build into the ship so that all you need to do is click somewhere, setting a target location, and your ship will decide which powering squares to use to get you there. I have not yet implemented that, because I am not quite sure how I want to do it yet. I should be able to make some headway on that tomorrow however.

As always, even though I feel like I got some good stuff done today, it is never enough. Still so much to do. Just gotta keep going.

01/12/14 Day 12: Vector Math
---------------------
Today was not so productive, as I spent a while re-learning how to use vectors to get the right target the ship. Currently, what the targeting algorithm does is the following for each individual energy square in your ship:

(MAKE PICTURES)


1) Get the target location in absolute world coordinates, and subtract from the energy square's center location, thus making a difference vector
2) Using the current angle of the energy square, convert the difference vector into a vector oriented about the energy square's local coordinate system
3) Give the newly oriented difference vector to the engines, and get thrust in the desired dimensions, depending on what engines directions are available for that energy square

Simple enough right? Except it hasn't been unfortunately. There are some problems which I am not yet sure how to solve. One is a LibGDX issue, in that the absolute coordinate system will resize itself to the zoom level. Meaning that the top left corner of the screen is set as (0, 0) regardless of zoom. This causes problems in that it creates a mis-match between actual world coordinates and perceived world coordinates.

Another issue, which is more basic and might make me have to scrap the movement stuff I currently have, is that the ship with multiple energy squares with various engine dispositions still spins like crazy when it tries to fly a target location, because different energy squares provide different levels of thrust and it seems to immediately get out of whack. Not good. So I need some way for the ship to stabilize itself and still head in the right direction.

01/13/14 Day 13: Down the rabbit hole
------------------------------
The issue of control has not been resolved. Not a lot of code written, but a good amount of head scratching over my notes, with lots of poorly drawn cartesian coordinate systems. My thoughts are still somewhat jumbled on this, but I'll see if I can explain the problems a little more thoroughly. 

So, we have a rigid body, the ship. The ship is made up of equally sized blocks, all square and all set at the same angle. Each block's density is (for now) the same as all the other blocks. However, the blocks can form irregular shapes, since you can connect them however you want. It has multiple points where forces can be exerted, or in other words, control points (in other other words, these are the energy squares I have been talking about). The way forces are exerted on the blocks is through 2D vectors, with an X and Y component. The available X and Y components of the force that can be exerted on each energy block is variable (dependent on the number of engine blocks).

What we end up having is an irregularly shaped rigid body, with multiple points of control with varying force. And we want to move this body to a target location efficiently using the available points of control, without rotation. In other words, imagine having 4-5 legs, all of varying lengths and on various locations on your body, and having to walk in a smooth manner. It would probably be tough. Add on to this the fact that these same energy squares will eventually be used for powering weapons as well, meaning an energy square could be powering an engine at one time and then a weapon at another, and you get a recipe for complexity.

So after typing all that, let's get to my current ideas on how to solve this issue, and the problems my solutions then raise. 

My first thought was that instead of dealing with each energy square every time we want to make a movement calculation, we could just sum all of the energy square X and Y potential forces into one overall potential force vector for the whole ship, centered on the center of mass of the ship (conveniently provided by Box2D's getWorldCenter() method), and then go from there. This could work, and would neatly eliminate any issues with rotation, because you would always be exerting a force on the center of mass. However, what I don't like about this is that it isn't a realistic simulation of the physics of a mult-engine ship, because it doesn't take into account any of the torque caused by different energy squares being variable distances from the center of mass. I'll call this the Single Force Vector solution. Pretty simple to implement, but not realistic. I'll leave it as a last resort.

(DRAW PICTURE OF ONE FORCE VECTOR SOLUTION)

My next idea was a little more complicated, but took torque into account:
- Get a target location, and convert that target location into a unit square vector relative to the ship's coordinate system [Link: http://www.wildbunny.co.uk/blog/vector-maths-a-primer-for-games-programmers/rotation/], this unit square vector is the (X,Y) direction that each energy square will fire it's engines
- For each energy square, in the X dimension, calculate the moment arm formula (Torque = moment arm length * force), where the moment arm length is distance from center of energy square to center of mass of the ship in the given X or Y dimension, and force is the available thrust for the given energy square in the X dimension, to calculate the torque that energy square will provide
- Repeat this process, only in the Y dimension
- Sum all of the torques
- You now have the total torque that would be exerted on the ship if all of the energy squares fired at the same target vector
- To avoid rotation, what would then be needed is some kind of torque matching, where we get the maximum amount of force we could from each energy square, but at the same time make sure to balance the negative torque and positive torque exactly, thus keeping the ship from rotating

(DRAW PICTURE OF CONSTANT TORQUE SOLUTION)

I call this the Equal Torque solution. I have not yet implemented this idea, but I am worried about the potential performance penalties (I know I know, premature optimization = evil and all that, but still, that is a lot of calculation), as well as whether this will actually result in consistent and controllable motion. I will try it out tomorrow and see what happens, but I have a feeling that this is going to be a difficult thing to get satisfied with, because really it is at the core of the gameplay mechanic of geometry-specific ship performance, where the shape of your ship design changes the way that ship flies and fights. That is the hook of the game in my mind, so I need the effects of ship design changes to really show through its movement behavior.

01/14/14 Day 14: N/A
--------------------
Didn't have time to do anything today. :(

01/15/14 Day 15: Blah
----------------
Today was worthless. I mostly just stared at the screen. Not sure how I am going to do this motion control thing. If I don't figure it out by this weekend, I am just going to implement a simple method, perhaps the first one I mentioned on Day 13, and just move on to the next thing. Still a ton to do, and I am already 1/4th the way through the 60 days. Ah.

01/16/14 Day 16: Double Blah
-----------------------------
I didn't really do anything today, spent most of the evening with friends.

01/17/14 Day 17: AHHHHHHHHHHHHH
-------------------------------
WHY CAN'T I FIGURE THIS CRAP OUT.

01/18/14 Day 18
---------------
There were a few issues with basic ship movement, so I fixed those. But still no fix for complex ship geometries.

01/19/14 Day 19
---------------
Today I took a break, and also began work on my C/C++ class homework assignment

01/20/14 Day 20
---------------
One third of the way through, things are getting kind of backed up with work and my C/C++ class, we'll see how productive I can be this week.

01/21/14 Day 21
---------------
Work and C/C++ assignment = no work done today.

01/22/14 Day 22
---------------
goto Day 21

01/23/14 Day 23
---------------
Today I at least had the time and energy to look at my code. Really, basic steering behaviors for simple shapes are still not working well. Right now steering can still be thrown off very easily by changes in angle, causing all sorts of errors.

01/24/14 Day 24
---------------
Got some sketches done to upload to this blog, that way I can better explain what I am saying. Will update some of the older posts. Otherwise, looking at trying to get a better way to apply forces to individual squares accurately, as currently there is a slight difference between what is calculated as the center of an energy square vs. where that center is in the box2D world, which means that when I apply a force at the calculated "center", there is a slight torque on the square and this can result in unwanted rotation.

01/25/14 Day 25
---------------
Still tweaking the navigation algorithm, but making progress. There seems to be some sort of oscillation problem when the ship is rotating where it won't maintain X,Y position, but only if it is spinning. I think this has something to do with converting coordinates from world coordinates to ship coordinates and back, but haven't been able to narrow down the root cause yet.

01/26/14 Day 26
---------------
Work/Class

01/27/14 Day 27
---------------

01/28/14 Day 28
---------------

01/29/14 Day 29
---------------

01/30/14 Day 30
---------------
Some progress at last! Basic navigation finally works when the ship rotates, but only if it is a uniform shape. Work will begin on non-uniform shapes this weekend.

01/31/14 Day 31
---------------

02/01/14 Day 32
---------------
Have a semi-working implementation of a rotation-based navigation algorithm, but it does not work with non-symmetric ship shapes, and often ends up in the ship spinning about wildly and off-target. I may have to something else.

02/02/14 Day 33
---------------

02/03/14 Day 34
---------------

02/04/14 Day 35
---------------
Lot of frustration today. I feel like I might need to rethink what I have been trying to do with the whole concept.

02/05/14 Day 36
---------------
I have decided to implement a simpler process for moving a ship, and am dropping the build your own ship features for now. It is disappointing, but my number one goal with this project was getting a "complete" game out the door, and as things stand right now I don't think I can do that if I focus on making every aspect of the game perfect. Moving forward, I will start with a simple ship design for the user and enemies, mouse control, and asteroids. I will still use Box2D and leverage some existing code. I may return to the ship-building game mechanic at some point, but first things first, I need to get a fully working game.

02/06/14 Day 37
---------------
Wow, I just found a game that has many aspects of the whole ship creation thing, and does them pretty well:

[Captain Forever](http://www.captainforever.com/)

I played this game for a bit, and I found it very fun, and it makes the ship-building aspect of playing very fun, while also intense, and it involves some thinking. The one part of my idea that is different is the idea of engine and weapon power being determined by size. In the Captain Forever game, new weapons and engines are picked up from enemies, but the relative power of any given weapon or engine is static.

All-in-all, it is a pretty bittersweet thing to see a game with so many of "my" ideas in it, so well executed. On the one hand, it is very cool to see the concept realized. But it is hard not being the one who created it. It is very rare to be the first one to an idea, and I knew that going into this project. However, the timing of this discovery is pretty funny, right when I decide I need to shift away from the ship-construction concept and instead focus on finishing a game, I come across a game with all the game mechanics I wanted. Oh well. I am going to push forward with a simpler "Asteroids"-style game, and worry about doing more later on.

The key to actually finishing this game will be forcing myself to move forward. Common advice I have found on other forums is to get something in a "good enough" state, and then leave it until you need to come back and polish it more. I was trying that earlier, but I got very much side-tracked. Simplicity is key, and by eliminating the need for a pretty complex control loop just to move from point A to point B on the screen, I'll be able to make a lot more headway.