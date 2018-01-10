---
layout: post
title:      "I'm back with my JQuery Front End Rails Project"
date:       2018-01-10 10:42:47 -0500
permalink:  im_back_with_my_jquery_front_end_rails_project
---


So its been a while but I've been busy coding and working through Javascript and JQuery.  Javascript in particular was much harder to grasp than I originally expected.  Something with the syntax just didnt stick like Ruby did (though I've heard this is common).  I was tempted to glance over the Javascript basics and just go through JQuery but during my initlal project review the instructor I was working with had me code a pure Javascript Todo list that you can checkout [here](https://github.com/ramell86/tasks-js-frontend)
Initially that was a pain but I am so glad that I did that since it forced me to get a better grasp of Javascript.  Plus I've found myself more engaged and focused working on a real project rather than doing excerses and labs one at a time.  It took some time but I was able to get a simple todo list that only starts with one HTML Div and the rest is added through Javascript. 

Onto the actual project -

I added Jquery to my rails app ["Team Player"](https://github.com/ramell86/team-player) that I worked out a few months ago.  This made the app even more "real world" since the page doesn't need to refresh for the basic functions and important features can all be done on the initial  home screen.   It of course still could use to more CSS /fonts and other touch ups but I am pretty happy with how its going so far with the functionality. 
[Yeah its still basic](<blockquote class="imgur-embed-pub" lang="en" data-id="kEwGpAt"><a href="//imgur.com/kEwGpAt"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>)

One of the areas I spent a good amount of time (and struggled) was displaying each team individually when you clicked on it.  I started out using the handlebars template and it works partially.  The problem I found and never really solved was that I needed to iterated not only over the team for all the games that it played but also the teams sports.  For some reason I was not able to get all of that sorted out easily with handlebars so I turned to the template literals in ES6 and it worked pretty easily.
```
 var team = new Team(team)                  
                  document.getElementById('teamshow').innerHTML = `<h2> ${team.name} </h2>
                  <p><strong> Sports this team plays:</strong></p>
                    ${team.sports.map(function(sport){
                         return `<li>${sport.name}</li>`
                     }).join('')
                    }</br>
                  <p><strong> Games: </strong></p>
                    ${team.games.map(function(game){
                      return `<li>Game Date:${game.game_date}</li>
                              Game Time: ${game.game_time}
                              </br>
                            `
                    }).join('')
                  }
                  <a href="/teams/${team.id}/games/new">Create Game for this Team</a><br>
                  <a href="/teams/${team.id}/edit">Edit this team</a><br>
                  <a href="/teams/${team.id}" rel="nofollow" data-method="delete">Delete Team</a><br>
                  `      
```

It took me a little bit of time to figure out the iterating with the map function and getting the backticks (`) in the right place but after a little but of playing around it was easy to create a template that can be used with all the teams.

Ultimately I need to add more readable time and dates to this project.  I've looked at the moment.js library but I can't figure out how to empliment it quite yet.  I also want to build out the functionality to allow additional users and team members to be show and allow them to indicate whether or not they will be able to attend each game.  This was the originaly reason for creating this app and I will continue to add these features as time allows.


