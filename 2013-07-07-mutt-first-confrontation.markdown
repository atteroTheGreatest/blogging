---
layout: post
title: "My first confrontation with mutt"
date: 2013-07-07 21:56
comments: true
categories: mutt mail gmail configuration files .muttrc
---

I don't like most of mail clients
===

Why is it so? They are usually overcomplicated and break my workflow. My main mail client is Thunderbird (I haven't done complete transition yet). I use it to check mails from all of my email addresses. And there are actually lots of them, five that I use nearly everyday. My primary adress is a gmail one. I wanted to get rid of google gmail web app, but it was so much more intuitive and better designed than thunderbird, that I ceased to do it.

Actually thunderbird is a real riddle for me. I now how to change them, install plug-ins, create new events in calendar, configure facebook-chat and so on, but I am still unable to make my email browsing comfortable. A disaster!

Why not gmail then? I don't want to give all of my correspondence into google hands. I wouldn't feel good with it. Next thing is - browsing emails in web browser is pretty distracting for me. I want to chat to my friends, I click on google plus. I also tend to stay on google gmail page way to long. 

I use KDE as primary windows manager and default mail client is a kmail. I admit that I haven't tried it. However I heard that it is similar to thunderbird(some of my friend claim that it is even worse), but I don't want to be forced to use a specific windows manager in the future, because I don't really know how would my future configuration look like.

It turns out that among my linux-using friends the highest esteem has a mutt.

What is mutt?
===
Mutt is a console mail client which is really good at what it does and nothing else. Its [homepage](http://www.mutt.org/) isn't really appealing. More useful for beginners can be this [overview](http://mutt.blackfish.org.uk/)

Actually to handle emails with mutt, you need something more than mutt. That might be surprising, because we are used to all-doing applications, but if we look at it from linux perspective it makes perfect sense.

You will need to:

+  fetch your emails
+  sort/categorize/filter your emails
+  see your emails
+  edit them
+  send

and mutt of course :).
Pretty much stuff and every element might fail. 

Mutt with gmail
===
I wanted to configure my mutt to work with emails, that I get on my gmail account. I was looking for some easy solution in the internet, because it's much easier to start with something than doing everything from scratch.

This [tutorial](http://www.andrews-corner.org/mutt.html) was most helpful for me. I did all those steps and ended up with pretty usable mutt but without my emails. The biggest problem for me was actually configuring procmail. It has regular expressions to sort emails and path to directories which aren't really intuitive - I've spent too much time to do it right and actually get some emails. One source of my problems was just plain ignorance - like using '~/' instead of '/home/me/'. This magic simply didn't work. 

Elements
===

So I ended up with [fetchmail](http://fetchmail.berlios.de/), [procmail](http://www.procmail.org/), mutt, [msmtp](http://msmtp.sourceforge.net/) and some not so bad [color configuration](http://therandymon.com/woodnotes/mutt/node58.html).

Some people recommend [maildrop](http://www.courier-mta.org/maildrop/) instead of procmail. I don't know yet what is better. However I know that procmail configuration syntax can be ugly and isn't intuitive at all, at least for me, so maybe in the future I would [migrate](http://www.wonkity.com/~wblock/docs/html/maildrop.html) to maildrop.

Conclusion
===

If you use your console terminal a lot, you would probably really enjoy mutt, because it's convenient to use in console pane/window, especially with [tmux](http://tmux.sourceforge.net/) which I started using recently. Mutt is really nice and does what it is supposed to do. Everything is really intuitive and easy and to do most common task you only use some simple keystrokes, no more unnecessary clicking!