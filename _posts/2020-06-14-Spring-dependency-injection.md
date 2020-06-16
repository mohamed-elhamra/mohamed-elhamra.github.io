---
title: Spring dependency injection
author: Mohamed Elhamra
date: 2020-06-14 14:00:00 +0800
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
    
    private String someData = "some data";

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

    private AsusHardDisk asusHardDisk = new AsusHardDisk();

    public AsusHardDisk getAsusHardDisk() {
        return asusHardDisk;
    }

    public void setAsusHardDisk(AsusHardDisk asusHardDisk) {
        this.asusHardDisk = asusHardDisk;
    }
}
```

Imagine if the class `Computer` no longer needs the class `AsusHardDisk` and wants to use `HpHardDisk`.<br />

Now, we are facing a problem because we will need to recreate the class `Computer` with the new hard disk.<br />

But when using the **dependency injection** you no longer need to instantiate the dependencies inside your classes, instead, the **DI** does all the work for you.<br />
**DI** is considered as a middleman between a class that needs another, especially **DI** makes our class `Computer` independent from creating the `HardDisk` class.<br />

In general, the **IoC container** lets you inject required objects in the runtime instead of the compile-time by the **dependency injection**, in order to make java classes independent of each other (loosely coupling) and frees them from object creation and maintenance.<br />

Basically, in Spring there are two types of DI:
* Setter dependency injection.
* Constructor dependency injection.  


# Types of Spring dependency injection

#### 1. Setter dependency injection

The dependencies will be injected with the help of the setters.<br />
**Example:**

```java
package com.melhamra;

public interface HardDisk {
    
    public String returnData();
    
}
```

```java
package com.melhamra;

public class AsusHardDisk implements HardDisk{

    private String someData = "some data from asusHardDisk";

    public void setSomeData(String someData) {
        this.someData = someData;
    }

    @Override
    public String returnData() {
        return someData;
    }
}
```

```java
package com.melhamra;

public class Computer {

    //Now we can work with any type of hard disk
    private HardDisk hardDisk;
    
    public Computer(HardDisk hardDisk) {
        this.hardDisk = hardDisk;
    }

    public Computer() {}

    public HardDisk getHardDisk() {
        return hardDisk;
    }

    public void setHardDisk(HardDisk hardDisk) {
        this.hardDisk = hardDisk;
    }
}

```

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;

@org.springframework.context.annotation.Configuration
@ComponentScan
public class Configuration {

    @Bean("asusHardDisk")
    public AsusHardDisk getAsusHardDisk(){
        return new AsusHardDisk();
    }

    @Bean("computer")
    public Computer getComputer(){
        Computer computer = new Computer();
        // DI using the setter
        computer.setHardDisk(getAsusHardDisk());
        return computer;
    }
    
}
```

If we compare  the class `Computer` used in the first section and the one used in this section we can conclude that:<br />
* The class `Computer` is no longer responsible for the instantiation of the dependencies.
* The dependencies are created by the **IoC container** using **DI**.

#### 2. Constructor dependency injection

In this, the DI will be injected with the help of constructors.

**Example:** Let us take the same example as of setter dependency injection but we will change just the configuration.

```java
package com.melhamra;


import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;

@org.springframework.context.annotation.Configuration
@ComponentScan
public class Configuration {

    @Bean("asusHardDisk")
    public AsusHardDisk getAsusHardDisk(){
        return new AsusHardDisk();
    }

    @Bean("computer")
    public Computer getComputer(){
        // DI using constructor
        Computer computer = new Computer(getAsusHardDisk());
        return computer;
    }
}
```

> **Note:** All the codes above are available via this link : [**DI Demo**](https://github.com/mohamed-elhamra/DI-demo.git)
<br />

**Process Flow:** The process flow of bean instantiation and injection of dependencies is given in the picture below:

<img src="/assets/img/sample/flow-di.PNG" alt="drawing" width="400" height="400"/>

# Summary

As you can see, DI has many benefits such as:
* Helping in Unit testing.
* Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
* Extending the application becomes easier.
* Helps to enable loose coupling, which is important in application programming.<br />

That was all for this blog, I hope you enjoy it and you understood all the points that we have touched on.



























