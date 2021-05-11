---
layout: project
title: Speedrun
course_name: Game Design
course_number: CS 1666
project_name: Super Speedrun Ultimatum
github: https://github.com/Speedrun-Game-Dev-Pitt-CS1666-Fall-2020/Speedrun
permalink: /projects/speedrun

first_p: The goal of CS 1666 was to– over the length of the entire term– create a fully functioning game of our choosing from scratch… and I don’t mean Scratch the programming language, I mean writing literally all of the game code (except for the SDL2 library) in C++ by ourselves.
---

{{ page.first_p }}

As a means of simulating small game studios, the students of CS 1666
were divided into four 10-person teams. Each of these teams was then
subdivided into three subteams. I was placed on the Networking subteam
for the Speedrun project. The other two subteams on our project were 
the Physics subteam and the Procedural Level Generation subteam.

The project had to run on Linux, so each of the team members worked in 
his own virtual machine. In addition to this, the game had to be 
*frame rate independent*, meaning a player's movement would not be limited
by the performance of his or her computer. Thanks to the Agile SCRUM SDLC 
methodology, our project's development occurred in week-long sprints. Each 
week, we would rotate the role of Scrum Master to a new student.

The Scrum Master was responsible for drafting up the goals of each subteam. 
These goals were negotiated with the professor to ensure our sights were 
set on something challenging yet achievable for that week. One of our early 
goals-- which was the responsibility of the Networking subteam-- was to create 
a menu for the game (as seen below).

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/speedrun/Menu.gif" alt="menu gif" />
    <figcaption>
        The menu is just one massive state machine. Do you like the logo? I made it!
    </figcaption>
</figure>

Once the other subteams had created players to move around and terrain 
to move on, the Networking subteam began work on a rudimentary message 
passing system that would send one player's position from the client 
to the server. At this point, only one connection could be handled by 
the server at a time.

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/speedrun/Message.png" alt="the one with red terrain" />
    <figcaption>
        A message containing the player's coordinates is passed from the 
        client terminal (on the left) to the server terminal (on the right).
    </figcaption>
</figure>

Over time, our server code evolved into a beast (in a good way) with the 
capability to manage a maximum of four players and 10 terrain obstacles 
at once. Each player passes his or her game-world coordinates to the 
server. The server then propagates this information to all other clients. 
Upon our first attempt, we encountered some issues with displaying the 
replication.

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/speedrun/ReplicateObjects.png" alt="the one with ice and rock" />
    <figcaption>
        This image depicts two separate clients overlayed on top of each other for testing.
        The colored circles correspond to the same objects replicating to the wrong locations.
        The client's player always appears in bright blue from their point of view.
    </figcaption>
</figure>

After fixing the mathematical errors in our display calculations, however,
the players appeared properly across screens. Don't tell the professor, but 
obstacles were never technically replicated 100%. They follow a deterministic 
path, so we simply replicated the spawn locations of each obstacle. Doing 
anything else would've required a rework on the part of the Physics team, and 
it was too late in the project at this point to do anything of the sort.

Our final commit to the project featured networked multiplayer (which works 
over both localhost and LAN); randomized maps with bouncy, icy, and normal 
terrain; and obstacles such as boulders, moving platforms, and rooms.

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/speedrun/Bounce.gif" alt="demo" />
    <figcaption>
        This is a demo of seed 12345, featuring a bouncy moving platform, a boulder, 
        a room, and a mix of icy and normal terrain.
    </figcaption>
</figure>

<p class="no-indent">Just for fun, here's our credits sequence:</p>

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/speedrun/Credits.gif" alt="credits reel" />
    <figcaption>
        The closing credits are sped up to reasonably fit within the GIF format.
    </figcaption>
</figure>