---
layout: post
title:  "Sinatra Project Completed"
date:   2017-08-03 21:45:35 +0000
---

Well I just submitted my Sinatra Portfolio project and am pretty pleased with what I was able to create.  My project is a simple task list (not a revolutionary idea by any means) but it was great to create something very close to a real world web application.  After a little bit of struggle I found that I was generally able to get new features like editing and deleting items working after a few trial and errors.

[Homepage](http://imgur.com/D2JN4oF)

The nature of this post will be a “iwhat I wished I understood better post” that maybe will help other students that are starting to work on their sinatra app.  The main thing I found invaluable was looking at previous labs and lessions (like Sinatra NYC and the Fwitter project).  This let me visualize how things were supposed to look since this project was truly from scratch. These types of CRUD (stands for: Create, Read, Update, and Delete) apps follow a similar flow and routing so in many cases its simply changing a few things to fix your models and functionality.  
```
class Usertask < ActiveRecord::Base
belongs_to :user
belongs_to :task

end
```
One area that I struggled on and I think others have trouble with is the has_many relationship.  I feel like I understood it from an analogy or a conceptual level ( ...and author “has many” books but a book has only one author).  The difference is when your creating something yourself, sometimes its not a clear as that relationship.  For example, my app has 3 models: Users, Lists, and Tasks.  A User has many Lists but also has many Tasks (through Lists). A List belongs to a User but has many Tasks and a Task simply belongs to a list.  Through some trial and error I created a join table called UserTasks which helped with the has many through relationship that User’s and Task’s have for each other.  Join tables always will have a “belongs_to” for each model in the title.

[Screenshot](http://imgur.com/EK26u64http://)
