---
layout: post
title: "Canvas with javascript and coffee"
date: 2013-06-30 16:21
comments: true
categories: programming web web-development canvas coffee javascript
---

Javascript is a bit awkward. The language itself is pretty powerful, but it has an obscure syntax. This week I decided to learn some coffee script which is a cure for javascript ugliness.

Resources
===
Coffee has good learning resources, try:

[official site](http://coffeescript.org/)

[interactive ebook](http://autotelicum.github.io/Smooth-CoffeeScript/)

and plenty of websites such as:
[this one](http://www.ibm.com/developerworks/library/wa-coffeescriptcanvas/) where you are creating game of life on canvas.

Beauty
===
Coffee is really pretty. Syntax is pretty simple and has lots of sugar. It uses whitespace semantically, similar to python. It make it more elegant and readable, however it can't be compressed easily. By compression I mean cluttered source code which is often used in web-development production code.

List comprehensions and classes syntax is also very nice. It speeds up development and makes code more readable. 

Availability
===
It can be embedded in browser directly or first compiled to js and then embedded as a regular js file.

Installing coffee is easy. You only need nodejs and npm.

For complete beginners [this](http://blog.teamtreehouse.com/the-absolute-beginners-guide-to-coffeescript) can be a nice starting point.

Canvas
===
Canvas makes js and coffee real fun.

For the beginning I recommend this [ tutorial ](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Canvas_tutorial)

My goal was to build a tetris on a canvas with coffescript. I made some progress and actually built a simplified version - which was at least resembling real tetris ;), but it needs polishing and second thought. 

I learned that using classes in coffee script isn't usually the best idea. It can be tricky if you are used to classical concept of classes such as in C++ and python. Coffee is more functional oriented and it should be our approach.

Alternatives
===
You should be aware that there are also different [choices](http://jster.net/blog/js-alternatives-coffeescript-dart-typescript#.UdnEHJB8SZo), which one is the best? It's hard to guess and even harder to try them all.

For example I recently stumbled upon [gorilla-script](http://ckknight.github.io/gorillascript/).

It's easy to get overwhelmed by all these possibilities, but actually this abundance can help us to find a language which really suits us the best.