---
layout: post
title:  "The magic of Rails layouts "
date:   2017-09-05 21:49:05 -0400
---


Whats so exciting about rails layouts?  It simply allows you to keep a "theme" throughout your rails website which is great for branding whatever type of site you have but even more so its easier on the developers to create/maintain the site.  You see, instead of manually changing every navbar font for all your views, you can simply update the layouts/application file and that theme will be carried throughout the views that are allowed to use it. 

Simple example below:

Lets say you are trying to have the same header for your blog that is titled "The Best Blog in the Universe!" and of course you want that on each page.  in the views/layouts/application file you can input that title in `<h1>` text.  

`<h1>The Best Blog in the Universe!</h1>`

then you would add the `<%= yield $>` statement will allows Rails to inject the content for the action (which will pull up the views from the controller)

It would simply look like this 


`<h1>The Best Blog in the Universe!</h1>`
`<%= yield $>`

Now the content in your index action, for example, will show up below the headline on your site.  It will default to this unless you use and specify a new layout to use.  In most cases though, you will be using one layout and then creating the views to customize the various parts of the site.  

Routing would look like this:

```
Rails.application.routes.draw do
get 'index', to: 'posts#index'
	```

It would pull up the index action through the posts/index view.

