---
layout: post
title: Building a RESTful API with Go (Part 1)
---


Last week I decided that I wanted to learn more about Go. Since it was lunch time, I figured I’d use Go to write a simple backend API for an app that lists a bunch of different sushi rolls and their ingredients. It seemed like it would be an excellent way to get used to the syntax of the language and also learn how to use it in a practical application. My first step was to watch a bunch of tutorials on youtube.

# Step 0 — Setup Your Environment

Before doing anything, we need to have Go installed on our machine. I'm not going to go into detail about that here. If like me, you are starting from zero, you can check out the [documentation](https://golang.org/) or [this tutorial](https://youtu.be/5qI8z_lB5Lw) which I found helpful. It's pretty easy, the only significant difference with Go is that all of your projects reside in the same folder on your computer which is called your Go Workspace.

# Step One — Basic Structure

![1*McQQ9efunX_0JKb0-8DbMQ.png](https://miro.medium.com/max/1000/1*McQQ9efunX_0JKb0-8DbMQ.png)

At the top, we have the package declaration. In this case, we are using main which tells the compiler that this will be an executable file. If we were making a library, we would declare a name for it here and this would be the package name we would use whenever we accessed the functions later. For example, if we wrote `package maki` and then wrote a function called `AddWasabi()`, we would call that function with `maki.AddWasabi()`.

Next, we have the `import` keyword. This is where we list all of the libraries that we will use. The libraries’ names will go inside the parentheses as strings. For example, if we needed our `AddWasabi()` function, we would need to put `"maki"` here.

Finally, our `main()` function. Since this will be an executable file, `main()` is what will get called when our program runs. In other words, this is where the magic happens!

# Step Two — Let’s Make a Model

![1*B4uS20rQ3dm5Gco8oWC1DQ.png](https://miro.medium.com/max/1000/1*B4uS20rQ3dm5Gco8oWC1DQ.png)

Since we want to be able to render our data as json, we need to add `"encoding/json"` to our import statement.

Next, we need to create a model to represent our different sushi rolls. We will do this above our main function, and we will use a struct. A struct is used for Object Oriented programming in Go. It’s a user-defined data type that contains a collection of fields. It’s kind of like a class in ES6, in that it can have methods and properties that we define. To define a `struct`, we use the `type` keyword, an identifier for our new data type, and the struct keyword followed by curly braces containing the desired named properties.

> Source: [@johnteckert](https://medium.com/@johnteckert/building-a-restful-api-with-go-part-1-9e234774b14d)