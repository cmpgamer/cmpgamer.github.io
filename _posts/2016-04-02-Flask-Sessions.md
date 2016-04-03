---
layout: post
title:  "Flask Sessions"
date:   2016-04-02 23:15:00
categories: CPSC350
color: red
---

Sessions - It's needed to track you online

# Sessions

So since I talked about the more basic parts of Flask, I will talk about Sessions. Sessions in Flask are a bit annoying as I've found out the more and more I've used them. They are consistent only when they need to be. They tend to be sporatic when using Javascript with your website. That being said, let me delve deeper into sessions.

# Why keep a Session?

You might have heard of "cookies," for websites. Cookies are little pieces of information that websites use to track a user and their current "session" on a website, hence how Session was named. Sessions are useful if you want keep a user logged in on your site or to personalize what each user sees when they are logged in.

# The Good

Sessions are good for tracking users. They are very easy to handle in Flask but harder with JavaServer Pages, for example. The data in a session is stored in a Python dictionary called session. To modify it, you need to create a new key and store some value in session.

``` Python

session['username'] = username
session['id'] = id

```

# The Bad

Sessions in Flask are sporatic. It's hard to know when your Sessions are working or if they are broken. This only seems to happen when using Javascript to handle sending some data back and forth from the frontend to the backend. Sometimes when you refresh a page on your site, the session gets deleted, but that shouldn't happen. Cookies and Sessions should be persistent until you close the website, not refresh the page.

# My Thoughts

Sessions are needed for any website to function in some easy conherent manner. Some websites handle Sessions differently than websites that use Flask. I personally am not a fan of Flask's sessions, but I had to use them in order for my websites to function properly.

Other ways to store sessions after a bit of research is to use Redis to store Session variables in a small "database." It's not really a database that is created, but more of a container to store all current sessions from what I understand.

