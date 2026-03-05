+++
date = '2026-03-05T11:35:39+01:00'
draft = true
title = 'My first Cybersecurity experience IRL'
tags = ["Cybersecurity", "Pentesting"]
+++


# My week in cyber

Hi, this week has been very interesting. I've, for the first time in my life, found multiple vulnerabilities outside a controlled enviroment such as HTB, or insecure w11 machine.

## Twitter guy
The first one was pretty easy. I was on twitter doomscrolling etc, and i found a post about someone that created a simple keylogger and they shared the github repo. I looked at the code out of curiosity and found nothing interesting, so i started digging all the other repos.  

I found one that had a connection with the telegram API and I started searching an exposed token or something. There wasn't any.... that's good, except that there actually was the tokens. Altough they weren't exposed on the updated code they were on the commit history.  

I looked at the history of the file that handles the token and there they were. All of the tokens.
But, of course, being old commits those tokens sure are expired, well, they were not. I created a simple python script to send a message through the Telegram API and boom RESPONSE -> 200 OK  MESSAGE SENT.

Damn, poor guy. But as a responsible fella that I am,  I just sent him a  message, actually like 15 (to take the guy's attention), explaining that in that repo in that file in X commit, the API token is visible.

He actually read the messages and changed the visibility of the repo to private. That was cool, I kinda feel like a hero ajjasjsjsj.

The best part is that this dude actually goes on twitter posting about good cybersecurity practices and whatnot. In spain we say "En casa de herrero cuchillo de palo"



## Company

The other experience of this week was actually a "full" pentest, and I say full on quotes because Im not fully qualified to perform a full pentest, i dont have enough knowledge YET...

So, I got authorization to perform a pentest on a website. I first started by enummerating, clicking things, looking for forms, etc. Then I started looking at the requests that were made when completing a form. Found the backend API.  

The header revealed that it was written in python, so i tried `url/docs` hoping that they were using auto-documentation by fast-api. THEY WERE. And for my luck, all endpoints where ✨_unauthenticated_✨.  

There was an endpoint for the users like `/users/id/{id}` so i created a simple script to dump all users. No delay no nothing full power, making all petitions as fast as possible. There was no prevention to that.... So i obtained the data of all of the 900 users. 
The data contained ID(spain identity document), full address, phone, mail, full name, etc. That was a goldmine. 

That was the biggest and easiest finding ever.

I also found that the WP-API could list all of the wp-users and the xmlrpc.php service was enabled, allowing a targeted brute force attack.


## Summary


It was a fun week, actually got the motivation to start studing cyber again. Let's see how long does that motivation last....


Remember to always secure/block services by default and keep your secrets.. secrets. 

### Stay safe! - gjx00
![lock-in monkey](/home/runner/work/blogfolio/blogfolio/static/images/blog/lock-in_monkey.png)