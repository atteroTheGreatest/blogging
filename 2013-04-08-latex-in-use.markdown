---
layout: post
title: "Latex in use"
date: 2013-04-08 17:43
comments: true
categories: 
---

##Problem - how to write a good report
Good report should look at least okay. My (and my partners) reports used to look quite ugly.

They weren't well formated and we know nearly nothing about typography and we are usually too busy
to think about working on details for long hours. Instead we want to focus on computation and diagrams.

Writing lab reports is quite tedious in editors like MS Word or even Libre Writer (I'm a linux
user, so I use the second one). There's to much clicking and searching for symbols etc.

##Solution
[LaTeX](http://en.wikipedia.org/wiki/LaTeX)

I heard from lots of people that latex is a nice tool for writing articles and publications. My partner had even some experience in it.

Two days ago I thought: "Why not try it now? With this small report?". I decided to do it and my partner agreed to help me.

But as you probably know, latex isn't so easy as libre writer...

##Learning Latex
It turns out to be lots of resources to learn latex.
A good example is wikipedia [wikibook on mathematics in LaTeX](http://en.wikibooks.org/wiki/LaTeX/Mathematics).

There are also many websites with tutorials and quite a lot of books.

In my opinion if you are a beginner, it's a good idea to install a latex ide. I tried a Texmaker. Texmaker is written in QT and available on all platforms.
It even was in my repository (and I don't have ubuntu, but some odd, rare linux). It's got a good documentation and is pretty intuitive. My workflow in latex boosted.

##Problems
First problem I encountered was encoding. I wrote my report in Polish, a language which contains lots of strange characters i.e. "ę", "ó" and they were invisible in pdf I generated.

Quick search in google helped. There are packages for encoding! One with utf-8 helped.

{% codeblock %}
\usepackage[utf8]{inputenc}
{% endcodeblock %}

My second problem was inserting tables. I had to create a fancy table with spanning cells and wrapped content.
Latex is not table friendly by default. I even tried to use my Texmaker ide, which have table wizard, but it was tedious and didn't
give a desired effect. Happily, solution wasn't so hard - I found a detailed wikipedia wiki page on tables, which helped a lot!

It turns out that documentation is very good:
[arrows](http://www.access2science.com/latex/Arrows.html),
[symbols](http://www.access2science.com/latex/Binary.html),
[more on symbols](http://ia.wikipedia.org/wiki/Wikipedia:LaTeX_symbols)

All you need is in the internets.

Asking question is not so hard:
[tex forum](http://tex.stackexchange.com/questions )
because community is huge.

##Results
My report look quite impressive.

I learned lots of new things and I'm not tired of them and wanting more.
##Summary
Trying out LaTeX was a very good idea.
