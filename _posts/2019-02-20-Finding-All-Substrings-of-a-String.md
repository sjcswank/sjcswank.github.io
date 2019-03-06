---
published: true
tags: strings java code walkthrough
---
When I challenged my students to create a console word game one of the bigest challenges for them was finding all the valid words of a given string. I'm sure there are many ways to do this, as in most things programming. My approached followed the logic that finding all the possible words would be easiest if you broke the word into all possible combinations first. Well, determining what constitutes a valid words would be first on my to-do list, but after that, I'd break the word apart into combinations. 

Once you find all the combinations of the letters of the word, you can scramble those combinations and compare each permutation against the rules of a valid word. Seemed easy enough. Finding all the letter combinations proved not to be so easy for me. 

<!-- more -->

I have a touch of education in logic and discreet math so when I approached the permutations of a word I immediately understood the theory behind the problem- I'd done the same thing in college already. Putting the math into code was the only challenge. However, I hadn't seen something like finding substrings in college. I didn't already have the theory, or the math, to start me out. So. I needed some pseudo code. 

If you aren't familiar, pseudo code lets you write out each step your code will have to take in plain english. This allows you to think through each step and create a plan for your code without having to know the exact syntax you will use in the final code. It's a great starting point for any piece of code, especially when you don't really know what you need to do yet.

My peudo code ended up looking something like this:
- Starting at the begining of the input string
- Add first letter to an output string and print
- add next letter to the output string and print
- continue to end of string
	- begin at first and second letter 
	- skip one letter and add next letter to the output string and print
	- continue to end of string
		- begin at first and third letter 
		- skip one letter and add next letter to the output string and print
		- continue to end of string
        	- etc.
- Start again at the second letter of the string
	- begin at second and third letter 
	- skip one letter and add next letter to the output string and print
	- continue to end of string
    	- etc.
- Continue to end of string


This let me break the code apart into distinct steps and variables. For variables, my peudo code mentions an input string and an output string. The pseudo code also mentions looping through the letters of the input string. Since we will need to know where in the string we started each time, it makes the most sense to use a for loop with a built in index. Now we can start writing our real code.

	String input;
    String output = null;
    
    for(int i = 0; i < input.length(); ++i){
    	output = output + input.charAt(i);
        System.out.println(output)
    }




Next we need to start again with the first and second letter as the begining output string and repeat. We need to be able to tell our loop where to start looping now. Time to turn this into a function. 

	public static void AllCombinations(String input, int start){
      String output = null;

      for(int i = start; i < input.length(); ++i){
          output = output + input.charAt(i);
          System.out.println(output)
      }
    }


Like with the permutations, since we need to repeat code we already wrote, we probably want to use recursion here. Here's where I got tripped up. How do I tell the recursion where to start and what letter combinations to keep? We dont want to start over at the first letter, we want to start with the first _and second_ letters. It might be time to rethink our output string.

Since, when we end our looping, our output includes all letters, it would be convient if we could just tell our new output to set itself to the first two letters before starting the loop again. We can't do that with a String object, though. We _can_ do it with a StringBuilder object. We can append letters to the end of a StringBuilder object, we can cut a StringBuilder object to a certain length, and we can start a StringBuilder object with no characters. Perfect, that's everything we need from our output.

If we include the StringBuilder in our function, though, each recursion will recreate the StringBuilder. We don't want that- it would mean that for each turn of the loop we would start with a new, or blank, StringBuilder. To solve this issue we pass the StringBuilder as a parameter to the function.

	public static void AllCombinations(String input, int start, StringBuilder output){
    
      	for(int i = start; i < input.length(); ++i){
          output = output.append(input.charAt(i));
          System.out.println(output);
          output.setLength( output.length() - 1 );
      	}
    }
    
Lastly, where so we run our recursion? Right now, the code will only run up the string and print out each letter by itself. We need it to continue, after printing the letter by itself, up the rest of the string adding to the output. So our recursion should be after we print, but before we reset our output string.

	public static void AllCombinations(String input, int start, StringBuilder output){
        
      	for(int i = start; i < input.length(); ++i){
          output = output.append(input.charAt(i));
          System.out.println(output);
          if (i < input.length())
    			allCombinations(input, i + 1);
          output.setLength( output.length() - 1 );
      	}
    }

This is not the only way to solve this problem. I don't even know if this is a particcularly good way to solve this problem. This is just _one way_ to solve the problem. Right now, I'm ok with that. While doing research on this problem I found lots of other ways to solve this. I did notice that many of them did not include _all_ the combinations. For example, in [these solutions](https://www.geeksforgeeks.org/program-print-substrings-given-string/) the result "AC" is never produced. I might, at a later date, compair this solution with others online for efficiancy and completeness.  Right now, I'm just happy to be one step closer to a word game. Make your way back here to see the next steps in that process next week!

Thanks for reading and Happy Coding!
