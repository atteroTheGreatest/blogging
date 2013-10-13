---
layout: post
title: "Learning JavaFx2 - Part 1"
date: 2013-04-16 10:32
comments: true
categories: 
---

###Motivation
One of my projects has to written in Java or similar JVM language (not python sadly). It's a rich GUI application and I had to choose 
appropriate framework to develop user interface. After some research I found JavaFx.

I first wanted to do it in [Groovy](http://groovy.codehaus.org/), dynamic language for JVM, but after I saw documentation of GroovyFx...
I decided not to, because lots of subsection of this documentation was simply empty.

My project is not exceptionally ambitious and I wanted to do GUI as easily and fast and possible and then focus on major functionality of my app. I have developed some GUI's before
in C++ and Python. And it was rather simple and intuitive process (I love [Pyside](http://qt-project.org/wiki/Category:LanguageBindings::PySide)!).

###First impressions
I remember that I had some problems. I encountered very strange behavior of Intellij Ide, it was switching off after attempts to launch javafx project and I still don't know why. After some re-installations (SDK from Oracle and Netbeans IDE, which has default support for javafx) I started learning from the book: [Pro JavaFX 2](http://www.apress.com/9781430268727) which kindly provides source [code](http://www.apress.com/downloadable/download/sample/sample_id/1253/).

I had custom installation of a development platform and I followed a tutorial, was it successful? Not. Some of the first examples from this
book just doesn't compile on my computer. I lost lots of time, and found out that further examples works. WUT?

###Philosophy
I think that's the main reason why JavaFX is so strange for me it's its javaland philosophy, which I'm not used to. I prefer thinking in terms of problem not in terms of framework. An approach where framework has so many solutions for me and is itself huge and has its own complicated philosophy is for me overwhelming.

Maybe I need more time for learning it and then using will be a piece of cake. I truly hope so. 

###Suprises
I read Pro JavaFx book to be able to build nice, simple and clean GUI. Documentation of Java libraries is usually not very friendly in my opinion, because it's usually automatically generated and there's too small
signal to noise ratio whith all those classes and methods I usually doesn't need.

Funny thing is that one of the first application examples is a metronome, which uses a lots of transitions, which are quite funny in javafx. There a class and factory for everything. I usually think in terms on 2D canvas, but there it's implemented in different way. Nodes are binded to transitions and there is no trace of canvas.

Binding in JavaFx is a bit overwhelming. I've seen already at least 60 methods of public api connected with it. Nightmare! But it's quite useful when you get used to specific way of thinking about dynamic properties, which are observable, have event handlers and so on.

Chaining and builders are quite handy but they're not my favorite way of building objects, why not a wisely
designed constructor? When construction of an object takes 50 lines of code, I simply get lost. 

Here is an example of such code:

``` java Some random node written in JavaFx 

VBox variousControls = VBoxBuilder.create()
      .padding(new Insets(10, 10, 10, 10))
      .spacing(20)
      .children(
        ButtonBuilder.create()
          .text("Button")
          .onAction(new EventHandler<ActionEvent>() {
              @Override public void handle(ActionEvent e) {
                System.out.println(e.getEventType() + " occurred on Button");
              }
            })
          .build(),
        checkBox = CheckBoxBuilder.create()
          .text("CheckBox")
          .onAction(new EventHandler<ActionEvent>() {
              @Override public void handle(ActionEvent e) {
                System.out.print(e.getEventType() + " occurred on CheckBox");
                System.out.print(", and selectedProperty is: ");
                System.out.println(checkBox.selectedProperty().getValue());
              }
            })
          .build(),
        HBoxBuilder.create()
          .spacing(10)
          .children(
            RadioButtonBuilder.create()
              .text("RadioButton1")
              .toggleGroup(radioToggleGroup)
              .build(),
            RadioButtonBuilder.create()
              .text("RadioButton2")
              .toggleGroup(radioToggleGroup)
              .build()
          )
          .build(),
        HyperlinkBuilder.create()
          .text("Hyperlink")
          .onAction(new EventHandler<ActionEvent>() {
              @Override public void handle(ActionEvent e) {
                System.out.println(e.getEventType() + " occurred on Hyperlink");
              }
            })
          .build(),
        choiceBox = ChoiceBoxBuilder.create()
          .items(model.choiceBoxItems)
          .build(),
        MenuButtonBuilder.create()
          .text("MenuButton")
          .items(
            MenuItemBuilder.create()
              .text("MenuItem A")
              .onAction(new EventHandler<ActionEvent>() {
                  @Override public void handle(ActionEvent e) {
                    System.out.println(e.getEventType() + 
                                       " occurred on Menu Item A");
                  }
                })
              .build(),
            MenuItemBuilder.create()
              .text("MenuItem B")
              .build()
           )
          .build(),
        SplitMenuButtonBuilder.create()
          .text("SplitMenuButton")
          .onAction(new EventHandler<ActionEvent>() {
            @Override public void handle(ActionEvent e) {
              System.out.println(e.getEventType() + 
                                 " occurred on SplitMenuButton");
            }
          })
          .items(
            MenuItemBuilder.create()
              .text("MenuItem A")
              .onAction(new EventHandler<ActionEvent>() {
                  @Override public void handle(ActionEvent e) {
                    System.out.println(e.getEventType() + 
                                       " occurred on Menu Item A");
                  }
                })
              .build(),
            MenuItemBuilder.create()
              .text("MenuItem B")
              .build()
           )
          .build(),
        textField = TextFieldBuilder.create()
          .promptText("Enter user name")
          .prefColumnCount(16)
          .build(),
        passwordField = PasswordFieldBuilder.create()
          .promptText("Enter password")
          .prefColumnCount(16)
          .build(),
        HBoxBuilder.create()
          .spacing(10)
          .children(
            new Label("TextArea:"),
            textArea = TextAreaBuilder.create()
              .prefColumnCount(12)
              .prefRowCount(4)
              .build()
          )
          .build(),
        progressIndicator = ProgressIndicatorBuilder.create()
          .prefWidth(200)
          .build(),
        slider = SliderBuilder.create()
          .prefWidth(200)
          .min(-1)
          .max(model.maxRpm)
          .build(),
        progressBar = ProgressBarBuilder.create()
          .prefWidth(200)
          .build(),
        scrollBar = ScrollBarBuilder.create()
          .prefWidth(200)
          .min(-1)
          .max(model.maxKph)
          .build()
      )
      .build();

```

It's too long and it's ugly and my head's starting to ache. 

###Summary
I really start getting used to JavaFx peculiarities. Maybe I'll create beautiful GUI with it. I would really try but it may take some time. Stay tuned!