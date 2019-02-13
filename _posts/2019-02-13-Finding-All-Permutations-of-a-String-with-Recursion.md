---
published: true
tags: strings java code walkthrough
layout: post
---
In my [previous post](https://sjcswank.github.io/Stings-and-Things/) I presented a series of exercises, culminating in a challenge to create a text based game. I promised I would come back with some of the solutions to those exercises, and so, here I am. Today I'm going to tackle the second exercise, which is about permutations of characters in a string.

- Write a function that outputs all possible permutations of a string. For example, the string “AB” would out put both “AB” and “BA”.

Ok, let's get started!

**All Permutations of a String**

Permutations of a given string are the posibilities for the order of the letters. In two letter strings, such as "AB", there are two permutations: "AB" and "BA". As the number of letters increases, so does the number of permutations. It's not a 1:1 increase, though, it's actually factorial. 

A list string of 5 characters has 5!, or 5 _factorial_, permutations. I know, that sounds like fancy math words, but all this means is that the number of permutations would be 5 x 4 x 3 x 2 x 1, or 120. All the positive numbers including and below the number of letters multiplied together. That's it. You can check out [this quick video](https://www.khanacademy.org/math/precalculus/prob-comb/combinatorics-precalc/v/permutation-formula) for a demonstration of and expansion on this idea.

Knowing what we are trying to acheive is always the first step in writing a function. We want a function that will take in a string of n length, and return n! permutations. Understanding how to find the number of permutations gives us a good clue on how to write the function: the pattern n, n-1, n-2, etc. When you see a formula that follows a consistant increasing or decreasing pattern it's a good indication that _recursion_ may be the right way to go.

**Recursion**

Recursion is when a function calls itself. You write a function that subtracts one from a number and multiplies the result by the first number: 5-1=4, 5x4=20. Then you notice you need to do the same thing with the answer of the subtraction: 4-1=3, 3x4=12. It doesn't make sense to try to write another function to do the same thing, so we'll want to call the original function we wrote. And when you want to keep the process going before getting your return statement, like in the formula for finding a factorial, you can just call your function inside itself. Let's take a look at the factorial first.

**A Function that finds the Factorial of a number n:**

	static int factorial(int n){

		if (n == 0) {   
			return 1;
		}
        
		else { 
    		return(n * factorial(n-1));
        }
 	}   



Let's go through the major concepts of this function:

	static int factorial(int n){
    
  **If the number has reach 0, stop and print the last number (always 1)**

	if (n == 0)    
	return 1;
      
  **Else Multiply the number by (number - 1) and run again**
  	
	else  
    return(n * factorial(n-1));    
 	}   



Let's walk through this function even deeper, with 5 as int n.
	
factorial(5)
    
	if (n == 0)  [5 does not = 0, skip to else] 
		return 1;    
  	else  
    
  //multiply the number by (number - 1) and run again

	return(n * factorial(n-1));  [return(5 * factorial(5-1))] 
 	}   

factorial(5-1)
    
	if (n == 0)  [4 does not = 0, skip to else] 
		return 1;  
        
   //multiply the number by (number - 1) and run again
 
  	else  
    	return(n * factorial(n-1));  [return(4 * factorial(4-1))]
 	}  
    
factorial(4-1)
    
	if (n == 0)  [3 does not = 0, skip to else]  
		return 1; 
        
   //multiply the number by (number - 1) and run again
 
  	else  
    	return(n * factorial(n-1));  [return(3 * factorial(3-1))]  
 	}  
    
    
factorial(3-1)
    
	if (n == 0)  [2 does not = 0, skip to else] 
		return 1;    
  	else
    
  //multiply the number by (number - 1) and run again
    	
        return(n * factorial(n-1));  [return(2 * factorial(2-1))]  
 	}  
    
factorial(2-1)
    
	if (n == 0)  [1 does not = 0, skip to else]  
		return 1; 
        
  //multiply the number by (number - 1) and run again

  	else  
    	return(n * factorial(n-1));  [return(1 * factorial(1-1))]  
 	}  
    
factorial(1-1)
    
	if (n == 0)  [1 does = 0]  
		return 1; 
    
The input return of each function call is as follows:
	5  (5-1)  (4-1)  (3-1)  (2-1)  (1) return 1 x 1 x 2 x 3 x 4 x 5 = 120

It is important to note that the return actually comes in reverse order. The function will go completely into the recursion and return from the last time it is called back to the first. Like stacking plates on top of each other, each return must be 'popped' off the stack from the top, in the order it was put on there: 1, 2, 3, -> 3, 2, 1.

We now know how to find the _number_ of permutations, next we can use this knowledge to find the actual permutations themselves. 

**A Function that finds All Permutations of a String**

    private static void AllPermutations(String permutation, String input)
    {    
        if(input.length() == 0)
        {
            System.out.println(permutation);
        }
        else
        {
            for (int i = 0; i < input.length(); i++)
            {    
                StringPermutation(permutation+input.charAt(i), input.substring(0, i)+input.substring(i+1, input.length()));
            }
        }
    }

Let's walkthrough this one concept at a time again:

    private static void AllPermutations(String permutation, String input)
    {   
    
**If there are no letters remaining, stop and print**

        if(input.length() == 0) 
        {
            System.out.println(permutation);
        }
        else
        {
        
**As long as we haven't reached the end of the word**

            for (int i = 0; i < input.length(); i++) 
            { 
            
**Start again with permutation + charAt(i), "everthing before charAt(i)" + "everything after charAt(i)"**

                StringPermutation(permutation+input.charAt(i), input.substring(0, i)+input.substring(i+1, input.length()));
            }
        }
    }
    


now String permutation is "" + charAt(i) and String input is "everthing before charAt(i)" + "everything after charAt(i)"



The input and return of each function call with "ABC" as String input:
1. ("", "ABC"), ("A", "BC"), ("AB", "C"), ("ABC", "") **return "ABC"** 
2. ("AC", "B"), ("ACB", "") **return "ACB"**
3. ("B", "AC"), ("BA", "C"), ("BAC", "") **return "BAC"**
4. ("BC", "A"), ("BCA", "") **return "BCA"**
5. ("C", "AB"), ("CA", "B") ("CAB", "") **return "CAB"**
6. ("CB", "A"), ("CBA", ""), **return "CBA"**


There is a great [article](https://javaconceptoftheday.com/permutations-of-string-in-java-recursively/) on [Java Concept of the Day](https://javaconceptoftheday.com/) that goes through the code more indepth. It also shows a great chart of the inputs and returns for this function. I highly recommend you check it out, especially if you are still struggling or want to see every line of processing written out.

Now that we have found all the permutations of any given string, we can start to look at finding all combinations of a string next. The two will set us up nicely for the game challenge as we progress. Remember to check back for the rest of the [Strings and Things](https://sjcswank.github.io/Stings-and-Things/) solutions soon. For now, pat yourself on the back- this post covers some heavy material and you made all the way through!

Thanks for reading, and Happy Coding!
