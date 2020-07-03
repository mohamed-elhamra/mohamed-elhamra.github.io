---
title: Session vs Token Based Authentication
author: Mohamed Elhamra
date: 2020-07-05 12:00:00 +0800
categories: [Blogging, security]
tags: [authentication]
---

<img src="/assets/img/sample/authentication.png" alt="drawing" width="700" height="300"/>

# Introduction 

--------------------------------------

As most of us know the  **HTTP** (HyperText Transfer Protocol) is a **stateless protocol**, meaning that there is no link between two requests being successively carried out on the same connection. Nevertheless, there is some situation when we need to remember the request sender as shown the following example :<br />

Imagine we have an e-commerce website and a user adds a product to his shopping cart after he navigates to another page, suddenly the product disappear from the shopping cart.<br /> 

So in order to solve this problem, we need to make the application remembering the user identity by implementing **JWT token** or **Session**.

# Authentication

Before talking about **Sessions** or **JWT** we need first to define the authentification which is a process of identifying the user identity in a web application, in other words, check if the user exists in the database then let him access to resources, if not show an error message.<br />

It answers the question: **Who are you?** 

# Authorization 

After a good authentication, the server needs to verify the user's permissions, in other words,  what the user can do, and cannot do in your application.<br />

It answers the question: **What can you do?**

# Session-Based Authentication

In the session-based authentication, the server creates a session for each user **authenticated** and keeps all information about the session in a table located in the server, this table holds two columns the first one for the **session id** and the second for the **session information**.<br />

After the session creation, the server will store the session id on a cookie in the browser's client, and when the user wants to send a request he needs to send also the cookie that holds the session id so that the server can know the user identity.

<img src="/assets/img/sample/server-session.PNG" alt="drawing" width="700" height="300"/>











