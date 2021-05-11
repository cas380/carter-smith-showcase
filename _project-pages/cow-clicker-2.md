---
layout: project
title: Cow Clicker 2
course_name: Web Apps
course_number: CS 1520
project_name: Cow Clicker 2
github: https://github.com/cas380/cow-clicker-2
permalink: /projects/cow-clicker-2

first_p: CS 1520 is a team-based, semester-long project class centered around web applications. It taught me how to make websites similar to this one (though not quite the same, seeing as this is a Jekyll site). My group created a game called <a href="https://cow-clicker-2.appspot.com/" target="_Blank">Cow Clicker 2</a>, which is hosted on Google Cloud Platform with a Flask backend and JavaScript frontend. 
---

{{ page.first_p }}

The goal of our game is for the player to click cows until he or she reaches Infinity points. 
This can be done by purchasing the Progenitor Cow, whom awards Infinity points to the player 
on click, in the Cow Store. There are many different cows to buy along the way, each with different 
gimmicky effects to help the player accrue large sums of points.

Thanks to being hosted on GCP, the project has access to Datastore to keep track of player data. 
Our Datastore is a NoSQL database which we index with a string representation of our User objects. 
This means each User object (a username and password combination) corresponds to player data. As 
a simple security measure, the password saved to the User object is a sha256 hash of the user's 
password. We can still evaluate whether the password was correct or not, but an attacker would have 
a hard time reverse-engineering the hash (if it were somehow obtained).

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/cow-clicker-2/database.png" alt="our database schema" />
    <figcaption>
        The User key corresponds to two items of player data: 
        a bitwise representation of the cows owned, and an integer corresponding to the current points. 
    </figcaption>
</figure>

The state of the player's cows is stored as a bitwise representation. This means we have to decode the 
bitstring in the javascript. This is done by using a simple bitmask. For example, if the player owns only 
Chonk Cow and Standard Cow, the cow state will be 9 (b1001). To check whether or not the game should load 
Chonk Cow into the pasture, it applies a bitwise AND between the cow state and CHONK_ENUM (b1000). If this 
operation results in a non-zero value (the bit is present), Chonk Cow is loaded into the DOM on the Pasture 
page.

<figure>
    <img src="{{site.url}}{{site.baseurl}}/assets/projects/cow-clicker-2/points.png" alt="cows in javascript" />
    <figcaption>
        This switch statement is responsible for calculating the points awarded by a given cow on click. 
        This is where the different cow effects come into play.
    </figcaption>
</figure>

The database operations (as well as cow clicking and Flask serving) had been successfully implemented 
by Milestone 1, but the fancy DOM manipulation and CSS did not come until later. My group gave a 
presentation in front of our class showing off the project and received 
the most engagement with the class out of all the groups. Unfortunately, there's no recording of this 
presentation, but due to COVID-19 (which impacted the US during this semester), the other two Milestone 
presentations are available to view on YouTube.

<p class="no-indent">The following Milestone 2 and Milestone 3 videos cover important project changes in detail:</p>

<table class="figure-wrapper">
    <tr>
        <td>
            <figure>
                <iframe width="560" height="315" src="https://www.youtube.com/embed/oGPRMQWm8Cw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                <figcaption style="width: 560px;">
                    During Milestone 2, we focused a lot of our effort on making a decently-styled site 
                    and patching up any security issues from Milestone 1.
                </figcaption>
            </figure>
        </td>
    </tr>
</table>

<table class="figure-wrapper">
    <tr>
        <td>
            <figure>
                <iframe width="560" height="315" src="https://www.youtube.com/embed/SeS60Rr8S-s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                <figcaption style="width: 560px;">
                    During Milestone 3, we expanded and balanced the effects of the available cows, 
                    as well as changed our site design to be more intuitive.
                </figcaption>
            </figure>
        </td>
    </tr>
</table>

<p class="no-indent">The code for each milestone is available as its own branch on the github repository.</p>