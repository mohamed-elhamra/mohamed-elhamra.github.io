---
title: Hibernate framework basics and architecture
author: Mohamed Elhamra
date: 2020-06-28 14:00:00 +0800
categories: [Blogging, hibernate]
tags: [hibernate architecture]
---

# Introduction 

--------------------------------------

Hello everyone!! 😃😃 <br /> 
In this blog, I will talk about one of the most popular ORM frameworks in the Java ecosystem, which is Hibernate, but I will mainly focus on the architecture of this framework, the core components, and their functionalities.<br /> 
So let's started.<br />

> 💡 ORM or object-relational mapping is the programming technique to map application domain model objects to the relational database tables.

# What is JPA?

After talking about Hibernate, we need first to understand the JPA.<br />
JPA or Java Persistence API is a standard for mapping Java objects to relational databases, which means that each object is represented as a table in the database, in other words, the Java objects can outlive outside the Java application and the JPA specification lets you define which objects should be persisted, and how those objects should be persisted in your Java applications, as well as via the JPA the developer can map, store, update, and retrieve data from relational databases to Java objects and vice versa.
