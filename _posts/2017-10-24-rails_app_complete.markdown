---
layout: post
title:      "Rails App complete"
date:       2017-10-24 23:18:04 +0000
permalink:  rails_app_complete
---


At least for the requirements on the Rails portfolio project - I am going to call this one complete.  That said I would like to expand it out with more features and (much) better front end styling so that it hopefully will be a beautiful app that people could use.

**Overview**:
This app is intended for use with sports leagues/adult rec sports leagues to help players and managers deal with their team's game scheduling.  Users can login and view all the teams the play for and click through to see all the games they have upcoming for their team.  Users can create a new game and the application will assign that game to the team.  

**Signup/Signin**
Part of the requirements for the app are to user OmniAuth to allow users to login to the app through a 3rd party (I chose facebook).  This adds to user convience and also increased security.  The user credentials are vetted through facebook, which to be honest, spends a lot more on security than me.  There is also the traditional signup/signin process setup through rails.  Validations help to ensure that unquie emails are being used for each account. 

Once logged in the homescrren will show all teams that the user(player) is assigned to.  the can then click on each team to view the schedule for each game.  There are links to create a new team and also create a new game.

The most difficult part of this project for me was getting the nested attribute of sports to be able to be added to a new team.  I had this setup as a Team Has_many Sports and a Sport Has_many teams. Both these relationships are through the join table Team_Sports.  Once I got my custom attribute for sports set (shown below), I realized that it changes the actual HTML on the view.  It shouldn't be a surprise that rails ends up changing the HTML but it was still neat to see the "real world" example of it in action.  Further it was nice to stumble on the realization myself.  The example is showin below:


**without** the attribute writer (or accepts_nested_attributes_for) the HTML generated is this

<a href="https://imgur.com/i03tGxS"><img src="https://i.imgur.com/i03tGxS.png" title="source: imgur.com" /></a>

**custom writer method for sports_attributes**

`def sports_attributes=(sports_hash)
    sports_hash.each do |i, sport|
          sport = Sport.find_or_create_by(:name => sport[:name])
          binding.pry
          self.team_sports.build(:sport => sport)
    end
  end`

**will give you this in HTML**

<a href="https://imgur.com/vpyUIyA"><img src="https://i.imgur.com/vpyUIyA.png" title="source: imgur.com" /></a>


**New Features I would like to add:**
Feature I would eventually like to add would be reminder emails or notices to allow the team's manager easily check to see who is able to play for each game.  Ideally each game would be able to show who can (or can't make it).  Traditionally this has been done through either a group email or a group text but in most cases you need to actually count the number of players that are 'in' in order to assure that you have enough players for the game.
