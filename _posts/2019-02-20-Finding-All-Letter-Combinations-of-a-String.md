---
published: false
---
When I challenged my students to create a console word game one of the bigest challenges for them was finding all the valid words of a given string. I'm sure there are many ways to do this, as in most things programming. My approached followed the logic that finding all the possible words would be easiest if you broke the word into all possible combinations first. Well, determining what constitutes a valid words would be first on my to-do list, but after that, I'd break the word apart into combinations. 

Once you find all the combinations of the letters of the word, you can scramble those combinations and compare each permutation against the rules of a valid word. Seemed easy enough. Finding all the letter combinations proved not to be so easy for me. 

I have a touch of education in logic and discreet math so when I approached the permutations of a word I immediately understood the theory behind the problem- I'd done the same thing in college already. Putting the math into code was the only challenge. However, I hadn't seen something like this in college. I didn't already have the theory, or the math, to start me out. So. I needed some pseudo code. 

If you aren't familiar, pseudo code lets you write out each step your code will have to take in plain english. This allows you to think through each step and create a plan for your code without having to know the exact syntax you will use in the final code. It's a great srting point for any peice of code, especially when you don't really know what you need to do yet.

My peudo code ended up looking something like this:
- Starting at the begining of the input string
- Add first letter to an output string and print
- add next letter to the output string and print
- continue to end of string
- Start again at the second letter of the string
- Continue pattern to end of string

This let me break the code apart into distinct steps and variables. For variables, my peudo code mentions an input string and an output string. The pseudo code also mentions looping through the letters of the input string. Since we will need to know where in the string we started each time, it makes the most sense to use a for loop with a built in index. Now we can start writing our real code.

	String input;
    String output = "";
    
    for(int i = 0; i < input.length(); ++i){
    	output = output + input.charAt(i);
        System.out.printline(output)
    }

Next we need to start again at letter 2. To accomplish this I wrapped the whole thing in another for loop. I set the index of the inside loop to that of the outside loop so that when we reach the end of the string and start again, we could start at the next letter. Then I refactored the index variables to follow coding standards. All that left me with:

	for(int i = 0; i < input.length(); ++i){
		    for(int j = i; j < input.length(); ++j){
		    	output = output + input.charAt(j);
		        System.out.println(output);
		    }
	    	output = "";
		}

Once I tested that code, I wrapped the whole thing in a function that passes the input string as a parameter: 

    public static void allCombinations(String input){

    	String output = "";

    	for(int i = 0; i < input.length(); ++i){
    		for(int j = i; j < input.length(); ++j){
    			output = output + input.charAt(j);
    			System.out.println(output);
    		}
    		output = "";
    	}
    }
    
Again I tested my code and made sure everything was still working as it should. Once everything was varified I raised one hand above my head, bent it at the elbow, and gave myself a little pat on the back for completing the code. You should do that, too. Right now.

This is not the only way to solve this problem. I don't even know if this is a particcularly good way to solve this problem. this is just how _I_ solved the problem. Right now, I'm ok with that. At a later date I may return and see iff I can compare to [this solution](https://javahungry.blogspot.com/2014/02/algorithm-for-combinations-of-string-java-code-with-example.html) for efficiancy. Right now, I'm just happy to be one step closer to a word game. Make your way back here to see the next steps in that process next week!

Thanks for reading and Happy Coding!