---
published: true
tags: strings challenges java exercises
layout: post
---
When I was first starting out in programming, one of the first things I learned was how to minipulate and search through strings. Algorithms that manipulate strings are pretty ubiquitous throughout all levels of programming. I'm going to go over some of the great tutorials out there on strings, mostly focusing on Java. Then, I'm going to give you a taste of the extra credit work I put together for my students when I was a TA. Let's have some fun with strings and things.

<!-- more -->

There are some great tutorials out there already, so I won't try to reinvent the wheel. Instead here is a list of some of the ones I found most helpful:

**[ToutorialsPoint- Strings](https://www.tutorialspoint.com/computer_programming/computer_programming_strings.htm)**
TutorialsPoint is one of my all time favorite tutorials websites. Their tutorials are always easy to follow and indepth enough without being too heavy. This tutorial goes through the basics of what a string actually is, some of the basic concepts when using strings, and how to create stings in Java and Python. It's a great starting point. 

**[W3Schools- Java Strings](https://www.w3schools.com/java/java_strings.asp)**
W3Schools is another go-to for me. Like TutorialsPoint, their wording is easy to follow and covers just enough material. They also add a lot of examples of actual code. Always a great resource.

**[Oracle's Java Docmentation- Strings](https://docs.oracle.com/javase/tutorial/java/data/strings.html)**
Documentation is always the best place for learning any language, but they can be a little hard to get used to. The Java Documentation on Strings is certainly indepth, and provides plenty of code examples, but is a little clunky to read. I reccomend getting used to documention as early as possible in your programming journey. It'll be unendingly helpful at all stages of your learning. 

**Expanding on Your Knowledge**

Once you have a good understanding of strings, and the functions that go with them, try your hand at these exercises. I wrote up these exercises for a Java development course I was a TA for. The students who were above the curve, like I know all of us can be, got lessons that expanded on the material. 

The following challenges extend on your knowledge of dictionaries and lists, iteration over strings, and regex, all important features of building accurate and efficient string functions. These challenges build on each other and I recommend you complete them in order- BUT if as you read through them one challenge jumps out at you or you think you can solve it easily, start there! Sometimes it is best to start with the easiest work first.

- Write a function that will take in a string and output all distinct character combinations from that string. For this example in the string "ABC" output would be "A, B, C, AB, AC, BC, ABC" as "AB" and "BA" would be the same combination.
- Write a function that outputs all possible permutations of a string. For example, the string "AB" would out put both "AB" and "BA".
- Put the previous two functions together and write a function that will take in a string and output all possible character combinations and their permutations from that string. Now, "ABC" would give: "A, B, C, AB, AC, BA, BC, CA, CB, ABC, ACB, BCA, BAC, CAB, CBA". 
- Write a function that compares a string to rules for the structure of a word. This function should include at least one regex (regular expression) that defines a valid word. I suggest you keep this limited for now, but a word must have at least one vowel and must be only alpha characters!
- Write a function that will compare a valid word to a list of known words.
- Write a function that will take in a single word string and tell the user why it is not valid. For example, if a user inputs “bth” the function should print “there is no vowel in this string”. If a user puts in “laughst” perhaps the function prints “there are more than three consonants in a row in this string!” Remember to limit your possible returns to the requirements of your regex from exercise 4.
- Write a function that will take in a string and add it to a list of known valid words.
- Write a function that will take in a single word string and return a list of all valid words that can be made from that string. 
- Extend that function to add all valid words to a list of known valid words.

If all that was easy peasy for you, maybe you should expand even further. If you have the skills to create a console program with prompts and user entries, try your hand at creating a console game with the previous functions. 

This game should start by generating a random, valid word of at least seven letters. The game should print that word, a description of a valid word (based on your regex function), and instructions to find all letter combinations from that word which create a valid word. The game should let the player know when a word they enter is not valid and why. The game should also keep track of the possible valid words and the valid words the player has entered. Once the player has entered all possible valid letter combinations the game should congratulate the player and end.

If you had a hard time writing any of these functions, don't dispare! I'll post my solutions in a follow-up post soon. Make sure you check back in for the solutions, and an example of the console game!

Thanks for reading, and Happy Coding!
