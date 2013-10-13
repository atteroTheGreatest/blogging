---
layout: post
title: "GUI development in scalafx "
date: 2013-05-06 18:05
comments: true
categories: scala, java, javafx, scalafx, programming
---

###Installation
There is a scalafx [webpage](https://code.google.com/p/scalafx/) and it has detailed tutorial how to [install scalafx and get started](https://code.google.com/p/scalafx/wiki/GettingStarted). However it is actually even simples as described there. When you have working scala environment (eclipse with scala IDE for example) make sure that you use jdk from oracle (includes javafx by default and you need javafx to use scalafx) and just download scalafx jars and include them in your project.

###Available learning resources
Creating gui with scalafx isn't hard when you know how to use it. 

If you know javafx you've probably seen ProJavaFX book. Good news! There's a [scalafx equivalent in source code](https://github.com/jsacha/ProScalaFX/)

A better scalafx API overview is [ensemble project](https://github.com/jugchennai/scalafx-ensemble).

###When help from available examples is not enough
Asking google doesn't provide many helpful examples. I tried to resolve some of my problems, but I couldn't find right answer usually. Which is different from for example problems with java, because there are usually lots of questions with answers. 

But... it's not so bad. Scalafx source code is available and well written and you can just skim it and get your answers or translate your problem to javafx problem and then look for answer in java community.

###Mixing scalafx with javafx
I didn't all issues in my code(I have some problems with responsivness with observable buffers) but I can already tell that scalafx works well with javafx.

I wanted to add some warning dialogs into my scalafx application, but scalafx or javafx don't support it by default. I found dialogs library for javafx and tried to use it to show dialog in my scalafx app. Guess what? It worked and doing it was really simple.

{% codeblock splitContentToSentences - MainApp.scala %}
import javafx.scene.control.Dialogs
(...)
new Button("Submit") {
	onAction = {e: ActionEvent => 
		val emptyFields = getEmptyFields() 
		if(!emptyFields.isEmpty) {
			Dialogs.showWarningDialog(stage,
			 	emptyFields.mkString(", ") + " cannot be empty.",
			 	"Book couldn't be added.", "Adding failure");
			}
		}
(...)
{% endcodeblock %}

Here's the library: [javafx-dialogs](https://github.com/marcojakob/javafx-ui-sandbox/tree/master/javafx-dialogs)

and descriptive [blog post](http://edu.makery.ch/blog/2012/10/30/javafx-2-dialogs/) about how to use it.

And I forgot to add - scalafx looks quite well (like javafx) opposed to scala swing which looks just horrible. Scala swing sounds nice, it's simple, is available by default, has scaladoc... but don't get deceived. Scala swing looks old, api makes strange suprises, and its development is a lie. Just use something else instead, for example scalafx.