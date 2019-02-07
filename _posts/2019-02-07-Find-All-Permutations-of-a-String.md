---
published: false
---
In my [previous post](https://sjcswank.github.io/Stings-and-Things/) I presented a series of exercises, culminating in a challenge to create a text based game. I promised I would come back with some of the solutions to those exercises, and so, here I am. Today I'm going to tackle the first three exercises about combinations and permutations of characters in a string.

- Write a function that will take in a string and output all distinct character combinations from that string. For this exampl in the string “ABC” out put would be “AB, AC, BC, ABC” as “AB” and “BA” would be the same combination.
- Write a function that outputs all possible permutations of a string. For example, the string “AB” would out put both “AB” and “BA”.
- Put the previous two functions together and write a function that will take in a string and output all possible character combinations and their permutations from that string. Now, “ABC” would give: “AB, AC, BA, BC, CA, CB, ABC, ACB, BCA, BAC, CAB, CBA”.

I'll present the solutions I wrote for my students and, where I can, provide links to other possible answers. Each solution will be followed by a short description of the code and it's function. In some cases someone else has already explained the code better than I ever could. I'll summarize and link to those explinations when that happens.

Ok, let's get started!

**All Permutations of a String**

Permutations of a given string are the posibilities for the order of the letters. In two letter strings, such as "AB", there are two permutations: "AB" and "BA". As the number of letters increases, so does the number of permutations. It's not a 1:1 increase, though, it's actually factorial. 

A list string of 5 characters has 5!, or 5 _factorial_, permutations. I know, that sounds like fancy math words, but all this means is that the number of permutations would be 5 x 4 x 3 x 2 x 1, or 120. All the positive numbers including and below the number of letters multiplied together. That's it. You can check out [this quick video](https://www.khanacademy.org/math/precalculus/prob-comb/combinatorics-precalc/v/permutation-formula) for a demonstration of and expansion on this idea.

Knowing what we are trying to acheive is always the first step in writing a function. We want a function that will take in a string of n length, and return n! permutations. Understanding how to find the number of permutations gives us a good clue on how to write the function: the pattern n, n-1, n-2, etc. When you see a formula that follows a consistant increasing or decreasing pattern it's a good indication that _recursion_ may be the right way to go.

Recursion is when a function calls itself. You write a function that subtracts one from a number and multiplies the result by the first number: 5-1=4, 5x4=20. Then you notice you need to do the same thing with the answer of the subtraction: 4-1=3, 3x4=12. It doesn't make sense to try to write another function to do the same thing, so we'll want to call the original function we wrote. And when you want to keep the process going before getting your return statement, like in the formula for finding a factorial, you can just call your function inside itself. Let's take a look at the factorial first.

**A Function that finds the Factorial of a number n:**

	static int factorial(int n){
    
    //If the number has reach 0, stop and print the last number (always 1)
  		if (n == 0)    
    	return 1;
        
  	else  
    //multiply the number by (number - 1) and run again
    return(n * factorial(n-1));    
 	}   

Let's walk through this function with 5 as int n.
	
    factorial(5)
    
	if (n == 0)  //5 does not = 0, skip to else  
		return 1;    
  	else  
    //multiply the number by (number - 1) and run again
    	return(n * factorial(n-1));  //return(5 * factorial(5-1))  
 	}   

	factorial(5-1)
    
	if (n == 0)  //4 does not = 0, skip to else  
		return 1;    
  	else  
    //multiply the number by (number - 1) and run again
    	return(n * factorial(n-1));  //return(4 * factorial(4-1))  
 	}  
    
    factorial(4-1)
    
	if (n == 0)  //3 does not = 0, skip to else  
		return 1;    
  	else  
    //multiply the number by (number - 1) and run again
    	return(n * factorial(n-1));  //return(3 * factorial(3-1))  
 	}  
    
    factorial(3-1)
    
	if (n == 0)  //2 does not = 0, skip to else  
		return 1;    
  	else  
    //multiply the number by (number - 1) and run again
    	return(n * factorial(n-1));  //return(2 * factorial(2-1))  
 	}  
    
    factorial(2-1)
    
	if (n == 0)  //1 does not = 0, skip to else  
		return 1;    
  	else  
    //multiply the number by (number - 1) and run again
    	return(n * factorial(n-1));  //return(1 * factorial(1-1))  
 	}  
    
The return of each function call is as follows:
	5 * (5-1) * (4-1) * (3-1) * (2-1) * (1)

We now know how to find the _number_ of permutations, next we can use this knowledge to find the actual permutations themselves. 

    private static void StringPermutation(String permutation, String input)
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

    private static void StringPermutation(String permutation, String input)
    {    
        if(input.length() == 0) //If there are no letters remaining, stop and print
        {
            System.out.println(permutation);
        }
        else
        {
            for (int i = 0; i < input.length(); i++) //as long as there is a letter left
            {    
                StringPermutation(permutation+input.charAt(i), input.substring(0, i)+input.substring(i+1, input.length()));
                //start again with permutation + charAt(i), "everthing before charAt(i)" + "everything after charAt(i)"
                //now String permutation is "" + charAt(i) and String input is "everthing before charAt(i)" + "everything after charAt(i)"
            }
        }
    }
    
