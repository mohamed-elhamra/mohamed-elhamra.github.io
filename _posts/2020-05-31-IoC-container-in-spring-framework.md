---
title: IoC container in spring framework
author: Mohamed Elhamra
date: 2019-08-09 20:55:00 +0800
categories: [Blogging, spring]
tags: [spring container]
---

# Introduction 

--------------------------------------

Today we will talk about one of the most frameworks in the world which is spring, but we will focus mainly on the IoC container of this framework.
In the spring framework, the IoC container is considered as the heart of the whole framework because it's responsible for the creation of the object,  wiring the object together, configuring these objects, and handling the entire life cycle of these objects from their creation until they are completely destroyed.<br />
So in the next paragraphs, we will clarify more how the container does all those works.

# Inversion of control (IoC)

After diving into other principles or notion we need first to understand what the IoC stands for.<br />
IoC or inversion of control is a principle in software engineering by which the control of the object is transferred from the programmer into the framework especially a container, in our case the IoC container.<br />

To understand this more, we will illustrate this principle by this example:<br />
Imagine you are a programmer, and you want to write a code to solve a problem, after diving into coding you make calls to a library to work with.
However,  by IoC, the flow is inverted because the inversion of control enables the framework to take control of the flow of a program and make calls to your code. 

Some advantages of IoC:
* Greater modularity of program
* Easy testing of code

Spring framework implements the inversion of control through different mechanisms such as: 
* DI (dependency injection)
* Service locator pattern
* Strategy design pattern
* Factory pattern

```
I will talk about these mechanisms in future blogs
```

# How did the IoC container work?

The spring container doesn't know how to instantiate our object alone so to make that we need to specify a configuration metadata to our container, this configuration can be specified through the XML file, Java code, Java annotations, then the spring container uses our POJO class as well as the configuration, and he can create the beans.

```
**Bean**: an object that is instantiated and managed by the Spring IoC container
```
