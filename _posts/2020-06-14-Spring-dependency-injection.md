---
title: Spring dependency injection
author: Mohamed Elhamra
date: 2020-06-14 16:00:00 +0800
categories: [Blogging, spring]
tags: [spring DI]
---


# What is DI ?

Hello audience, today I am going to discuss the spring dependency injection which is a design pattern used to implement the IoC in the [**Spring container**](https://www.mohamed-elhamra.me/posts/ioc-container-in-spring-framework/).<br />

Before talking about the implementation of this mechanism, I need first to define the dependency injection:<br />

> In software engineering, **dependency injection** is a technique in which an object receives other objects that it depends on. These other objects are called dependencies.<br />

That’s the [**Wikipedia definition**](https://en.wikipedia.org/wiki/Dependency_injection), I know that's not enough to understand, 
but I will give you an example to illustrate more this mechanism.

Suppose we have two classes, `Computer` and `AsusHardDisk`, and the class `Computer` uses some functionality of the `AsusHardDisk` class, so we need to create an object of `AsusHardDisk` inside the `Computer` to make calls to these functionalities, now we can say that class `Computer` has a dependency on class `AsusHardDisk`.


```java                                                    
package com.melhamra;

public class AsusHardDisk {
    
    private String someData;

    public AsusHardDisk(String someData) {
        this.someData = someData;
    }

    public String getSomeData() {
        return someData;
    }

    public void setSomeData(String someData) {
        this.someData = someData;
    }
}
```

```java
package com.melhamra;

public class Computer {

    private AsusHardDisk asusHardDisk = new AsusHardDisk("Data");

    public AsusHardDisk getAsusHardDisk() {
        return asusHardDisk;
    }

    public void setAsusHardDisk(AsusHardDisk asusHardDisk) {
        this.asusHardDisk = asusHardDisk;
    }
}
```





















