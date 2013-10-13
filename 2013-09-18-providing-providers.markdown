---
layout: post
title: "Providing providers"
date: 2013-09-18 22:52
comments: true
categories: devops servers linux hosting dedicated-server
---

###Remote with root access


It's just amazing to have your own remote server, where you can do whatever
you like. I'm used to use servers set up by someone else, which is usually
pretty comfortable - everything works and if not, someone else is worrying about it.

However, the day with my own servers has come.

###Where


In short period of time i tried: Amazon AWS, OVH, DigitalOcean and Hetzner.
I had problems on each of listed above.
In the nearest future I'm going to set up a virtual machine on Linode.

###EC2


Amazon AWS gives everyone free tier for one year. This is pretty cool. You can have a small
instance for free, running all the time! However, bigger instances are getting pretty expensive,
I think that I would recommend EC2 for ad hoc big needs, rather than normal servers.

Installing Ubuntu is pretty simple there. User interfaces aren't the most user friendly, but i'm
sure, that you can handle them after reading the manuals (lots of manuals!).

###OVH

They couldn't set up my machine. That sucks. I cancelled the deal after nearly a month of waiting.

###Digital ocean

I was pretty unlucky and set an instance on which I couldn't ssh. I tried a lots of times.
Further investigation proved the problem with Digital ocean routing. I asked support for help and got
answer pretty soon. There was an error during setup. Changing location to Amsterdam helped.

Over all, the digital ocean droplet(their naming scheme for virtual servers is pretty strange, but 
you would quickly get used to it) just works nicely and I'm really satisfied for what I get, paying
so little.

###Hetzner

They try to be nice, but have some serious problems with their infrastructure. I need rock-solid
service and they wouldn't able to provide it. I run into problems with my server after
trying to install gentoo from rescue cd. It didn't boot. Probably some issues with network configuration.

Probably... I wasn't able to check. Their console, which would be a real salvation, if it worked, was
just failing and failing. I had problems with everything, using interface, passwords and logging to my
own dedicated server.

Rough times.

###Is there any hope?

Overall it was a good idea to try all this providers. I gained some experience, I have configured instances
where I can deploy whatever I want and just try things out.

I plan to try out linode now. But having a
good, cheap instance on digital ocean is real win. I also enjoy my free tier on amazon aws (and other bonuses).

I also tried collocation by friends. Yep... my server 'skarpetka' hosted in Warsaw Hackerspace is currently down.
God knows why.


