---
published: true
tags: 'javascript, coding-journey'
---
I've been interviewing recently for positions as a Junior Developer and in every interview I've been asked the same question: what experience with JavaScript and React.JS do you have? Every time I have to be honest, and every time I feel it hurts my chances of getting hired. I have basically no experience with either, but I'm happy and able to learn anything you throw at me. I feel the reassurance that I can and will learn it just isn't enough. So, it's time I take a break from working on my other projects and start learning some JavaScript.

<!-- more -->

When I started learning how to code I did a little research on what languages and technologies I wanted to start with. I chose to focus on things like Java, Spring, and database connections. What I didn't realize was how important things like HTML, CSS, and JavaScript would be to the coding work I would be doing. I make web apps primarily and you can't complete them without at least some of the aforementioned. My recent interviews have taught me how important JavaScript and its various libraries are to web app development, even if I do want to focus on the back-end. Never one to be discouraged by large projects, learning or otherwise, I decided it was past time for me to dive into learning JavaScript.

I've only been working on learning JavaScript for a week. I feel like I've just scratched the surface of what there is for me to learn. Even still, somethings have jumped out at me as just plain cool. One of the first things that made me really sit up and pay attention to what JavaScript has to offer is how arrays are handled. Some of the built in functions just make life so much easier. It blew my mind the first time I came across the spread operator. When I found map() and filter() I almost cried. 

I hate hate hate collections. I know they're important, useful, powerful elements in any coding language I've seen. I still hate them. It took me forever to understand things like nested arrays. I still have to look up which type of collection is best for a given use nearly every single time. I just hate them. So when I saw how much easier it is for me to work with arrays in JavaScript I was so relieved. 

I could talk about my infatuation with JavaScript arrays for a while, so that’s exactly what I’m going to do. I’ve got an ever growing list of things I find cool about arrays which I thought I would share with you. Hopefully you’ll find a love these big little variables as much as I do, if you don’t already.
Now, without further ado, allow me to introduce-

**The JavaScript Array**

Arrays in JavaScript started out pretty much like I learned in Java- a variable that holds more than one value. One step further and I already had an inkling that I was going to like arrays better in JavaScript than Java. Declaring was easier for me to remember and understand.  


***Declaring Arrays***

Declaring an array in JavaScript goes like this:
	
	var arr = [“valueX”, “valueY”, “valueZ”];
	
Easy Peasy, much simpler than Java’s:
	
	int[] intArray = new int[]{1, 2, 3};
	

Still, it’s not that different, really. Declare that it’s a variable (which in Java means giving the type but in JavaScript just means stating it is a variable), name the variable, and assign values to the variable. Same idea, just a bit less typing. Still, my interest was already piqued. How easy could arrays be in JavaScript? I wondered. 

Nested arrays were similarly easy to write out. Just stick some brackets around the nested array values.

	var arr = [“valueX”, [“valueA”, “valueB”, “valueC”], “valueY”];
	

Yeah man, I like this. I can see the nesting better. I can remember how to write this up. I might even be able to get to the point where I can work with arrays without consulting google every step of the way. 

Now, there are other ways to create arrays in JavaScript. You can use the Array() constructor, or create a new array with no parameters and add them later. It seems, from what I’ve seen around, that this simpler syntax is more common, though. Which is just fine by me.


**The Spread Operator**

Some of the things I hate the most about using arrays and the like have to do with accessing all or some of the elements in the array. Getting things out can be much more involved than putting things in. Like accesses all the elements of an array one by one to, for example, find the highest number.

In Java I was taught to iterate over the array, pull each value out one by one and compare for which is higher. It takes several lines of code, and there are plenty of ways for me to mess this up. It would be much easier if I could just put all the elements of an array into the Math.Max() function at one time- and maybe I can, but I haven’t found it yet. In JavaScript you can do just that with the Spread Operator. 

Instead of iterating one by one, you can input the entire array, spread as individual parameters, into the function. 
	
	var arr = [1, 5, 2, 4, 3];
	var arrMax = Math.Max(…arr); //passes 1, 5, 2, 4, 3 - assigns 5
	

There are much fewer ways for me to mess that up. I love it. I can’t wait to use it. I want to write up a program where I need to find the maximum of an array just to use it. And, of course, it works with any function, not just Math.Max(). Stick that ellipses before the name of the array when you pass it into the function and sit back and let the magic happen. 


**Array Functions**

In Java there are some methods built in to arrays that can be helpful. You can pass an array to the sort(arr) function to return, well, clearly, a sorted array. Once you’ve done that you can search for an element using binarySearch(arr, key), compare one array to another array with equals(arr, arr), or set all the elements of the array to the same value using fill(arr, value). Other than that, you can change the array to a List, which gives you a few more built in methods. That’s about it.
When I looked up more information on [arrays in JavaScript](“ https://www.w3schools.com/jsref/jsref_obj_array.asp”) I was surprised at how many methods were listed. In my mind arrays are simple, limited collections of values. In JavaScript they are still pretty simple, but not as limited. There are some really great, powerful methods ready to use right out of the gate. 

***arr.map()***

The arr.map() function is one of the first array functions I found. It lets you perform a function on each element in an array, one at a time, in order, and then return a new array with the function results, again, in order. So, if you wanted to square all elements in an array *without changing the original array* and assign those squares to a *new* array, you could use map().
	
    var arr1 = [1, 2, 3, 4, 5];
    
    const arr2 = arr1.map(x => x * x);
    //assigns arr2 = [1, 4, 9, 16, 25]
    
As you can see, and I cannot stress this enough, map() creates a new array, leaving us with the original array unchanged. If you aren't going to be using the new array you should probably not be using map()- try forEach() or some other function instead. 

***arr.filter()***

Like with map(), arr.filter() returns a new array, each element in the array it is called on will be put into a function one at a time, in order, with the results being assigned to a new array. With filter(), the function you use makes some caparison and returns a Boolean value. If the value is true the element being checked will be added to the new array. If false, the element will not be added. 

Often I find the naming conventions for methods in programing to be misleading, but filter() does exactly what it sounds like: filter out elements you don't want in the new array. A perfect example of this is creating a new array with only the even numbers from another array:
	
    var arr1 = [1, 9, 2, 4, 30, 15];
    
    const arr2 = arr1.filter(x => x % 2 === 0);
    //assigns arr2 = [2, 4, 30]
    
***arr.some() and arr.every()***

Sometimes all you need to know is if there is or isn't a certain kind of element in an array. I know how to test elements one by one in Java by iterating over the array. In JavaScript there are functions that will do the work for you: some() and every(). They both take in a Boolean expression and put out 'true' if that expression is matched in the array. Like it sounds, every() returns true if all elements in the array pass the Boolean check. Conversely, some() returns trues if one or more match the condition. 

Say I have an array of tweets. If I want to make sure all the tweets are less than 140 characters I could do something like:
	
    const pass = arr.every(x => x.length <= 140);
    
If *all* the elements are less than or equal to 140 characters pass will be set to true. Otherwise, it will be set to false. Cool. Just as cool is some(), which takes the same kind of inputs and returns true if at least one element in the array meets the requirements. So, if we have an array of the daily low temperatures for February, we could do the following to test if any day's low was below zero:
	
    const pass = arr.some(x => x < 0);
   

***arr.find(), arr.findIndex(), arr.indexOf(), and arr.lastIndexOf()***

As I've mentioned several times in this article, I hate having to loop through an array. The less I have to do it, the happier I am. That's why things like these four gems nearly make me giddy- less looping needed!

The first two, find() and findIndexOf() lets you find the first element, or the index of the first element, that passes a check you define. So, if in the example for some() above, we didn’t just want to know *if* the temperature fell below zero, but what that temperature was we would do:
	
    const pass = arr.find(x => x < 0);
   
If we wanted to know on which day the temperature fell below zero we could do:
	
    const pass = arr.findIndex(x => x < 0);
   
If we already know what temperature we are looking for we can locate it in the array with indexOf() or lastIndexOf(). With either we pass the value we are looking for and the function will search the array and return the first index where the value is stored. To begin searching from lowest index to highest use indexOf(). To begin searching from the end of the array to the beginning use lastIndexOf(). So, finding the first day the temperature was 32 would be:
	
    const pass = arr.indexOf(32);
   
Finding the last day of the month where the temperature was 32 would look like:
	
    const pass = arr.lastIndexOf(32);
   

**Going Forward**

After learning about everything I can do with simple arrays I have to admit, I'm more excited about learning more about JavaScript than I was when I started. Honestly, I had been *dreading* learning JavaScript for some reason I can't remember now. I'll keep track of other things I find to be cool about JavaScript as I go and check back in with more details. Until then,

Thanks for reading and Happy Coding!
