---
published: false
tags: 'javascript, coding-journey'
---
I've been interviewing recently for a position as a Junior Developer and in every interview I've been asked the same question: what experience with JavaScript and React.JS do you have? Every time I have to be honest, and every time I feel it hurts my chances of getting hired. I have basically no experience with either, but I'm happy and able to learn anything you throw at me. I feel the reassurance that I can and will learn it just isn't enough. So, it's time I take a break from working on my other projects and start learning some JavaScript.

<!-- more -->

When I started learning how to code I did a little research on what languages and technologies I wanted to start with. I chose to focus on things like Java, Spring, and database connections. What I didn't realize was how important things like HTML, CSS, and JavaScript would be to the coding work I would be doing. I make web apps primarily and you can't complete them without at least some of the aforementioned. My recent interviews have taught me how important JavaScript and its various libraries are to web app development, even if I do want to focus on the back-end. Never one to be discouraged by large projects, learning or otherwise, I decided it was past time for me to dive into learning JavaScript.

I've only been working on learning JavaScript for a week. I feel like I've just scratched the surface of what there is for me to learn. Even still, somethings have jumped out at me as just plain cool. One of the first things that made me really sit up and pay attention to what JavaScript has to offer is how arrays and objects are handled. The two have a lot in common in JavaScript. And some of the built in functions just make life so much easier. It blew my mind the first time I came across the spread function. When I found map and filter I almost cried. 

I hate hate hate collections. I know they're important, useful, powerful elements in any coding language I've seen. I still hate them. It took me forever to understand things like nested arrays. I still have to look up which type of collection is best for a given use nearly every single time. I just hate them. So when I saw how much easier it is for me to work with arrays in JavaScript I was so relieved. 

I could talk about my infatuation with JavaScript arrays for a while, so that’s exactly what I’m going to do. I’ve got an ever growing list of things I find cool about arrays (and a few about objects) which I thought I would share with you. Hopefully you’ll find a love these big little variables as much as I do, if you don’t already.
Now, without further ado, allow me to introduce-

**The JavaScript Array**

Arrays in JavaScript started out pretty much like I learned in Java- a variable that holds more than one value. One step further and I already had an inkling that I was going to like arrays better in JavaScript than Java. Declaring was easier for me to remember and understand.  

***Declaring Arrays and Objects***

Declaring an array in JavaScript goes like this:
	
	var arr = [“valueX”, “valueY”, “valueZ”];
	
Easy Peasy, much simpler than Java’s:
	
	int[] intArray = new int[]{1, 2, 3};
	

Still, it’s not that different, really. Declare that it’s a variable (which in Java means giving the type but in JavaScript just means stating it is a variable), name the variable, and assign values to the variable. Same idea, just a bit less typing but my interest was already piqued. How easy could arrays be in JavaScript? I wondered. 

Nested arrays were similarly easy to write out. Just stick some brackets around the nested array values.

	var arr = [“valueX”, [“valueA”, “valueB”, “valueC”], “valueY”];
	

Yeah man, I like this. I can see the nesting better. I can remember how to write this up. I might even be able to get to the point where I can work with arrays without consulting google every step of the way. 
Even better, making objects turned out to be just as easy as making arrays. Took me a minute to realize I wasn’t just making a map, though, because it looks like just a list of index : value pairings. No, it’s an object, which, when you think about it just holds a group of name : value pairs and some functions. So seeing how very similar the declaration for objects and arrays are shouldn’t be so surprising:

	var arr = {“nameX” : “valueX”, “nameY” : “valueY”, “nameZ” : “valueZ”};
	

Now, there are other ways to create objects and arrays in JavaScript. You can use the Array() constructor, or create a new array with no parameters and add them later. With objects you can do that same, use a constructor or create an empty object and add parameters later. It seems, from what I’ve seen around, that this simpler syntax is more common, though. Which is just fine by me.

**The Spread Operator**

Some of the things I hate the most about using arrays and the like have to do with accessing all or some of the elements in the array. Getting things out can be much more involved than putting things in. Like accesses all the elements of an array one by one to, for example, find the highest number.

In Java I was taught to iterate over the array, pull each value out one by one and compare for which is higher. It takes several lines of code, and there are plenty of ways for me to mess this up. It would be much easier if I could just put all the elements of an array into the Math.Max() function at one time- and maybe I can, but I haven’t found it yet. In JavaScript you can do just that with the Spread Operator. 

Instead of iterating one by one, you can input the entire array, spread as individual parameters, into the function. 
	
	var arr = [1, 5, 2, 4, 3];
	var arrMax = Math.Max(…arr); //assigns 5
	

There are so many fewer ways for me to mess that up. I love it. I can’t wait to use it. I want to write up a program where I need to find the maximum of an array just to use it. And, of course, it works with any function, not just Math.Max(). Stick that ellipses before the name of the array when you pass it into the function and sit back and let the magic happen. 

**Array Functions**

In Java there are some methods built in to arrays that can be helpful. You can pass an array to the sort(arr) function to return, well, clearly, a sorted array. Once you’ve done that you can search for an element using binarySearch(arr, key), compare one array to another array with equals(arr, arr), or set all the elements of the array to the same value using fill(arr, value). Other than that, you can change the array to a List, which gives you a few more built in methods. That’s about it.
When I looked up more information on [arrays in JavaScript](“ https://www.w3schools.com/jsref/jsref_obj_array.asp”) I was surprised at how many methods were listed. In my mind arrays are simple, limited collections of values. In JavaScript they are still pretty simple, but not as limited. There are some really great, powerful methods ready to use right out of the gate. 

***Array.Map()***
The Array.Map() function 
