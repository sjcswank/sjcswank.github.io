---
published: true
tags: strings java code walkthrough
---
Now that we have found [all the substrings](https://sjcswank.github.io/Finding-All-Substrings-of-a-String/) and [all the permutations](https://sjcswank.github.io/Finding-All-Permutations-of-a-String-with-Recursion/) of a string we can put them together and find all possible words from a string. That means all permutations of all substrings of the starting string. Let's review our previous two functions.

<!-- more -->

###[Finding All Substrings](https://sjcswank.github.io/Finding-All-Substrings-of-a-String/)

	public static void AllCombinations(String input, int start, StringBuilder output){
        
      	for(int i = start; i < input.length(); ++i){
          output = output.append(input.charAt(i));
          System.out.println(output);
          if (i < input.length())
    			allCombinations(input, i + 1);
          output.setLength( output.length() - 1 );
      	}
    }
    
###[Finding All Permutations](https://sjcswank.github.io/Finding-All-Permutations-of-a-String-with-Recursion/)

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

If you're just joining us, click those links to check out the full walk-thru of each function. These functions provide our starting point. We'll need to do some refactoring and put together a new function that encompasses both existing functions, but at least we aren't starting from scratch.

The refactoring is fairly easy to define- we need to have the functions return a list of it's results, instead of just printing them. Implimenting this in code is pretty easy for AllCombinations. So let's look at that first.

AllCombinations now needs to return a list of all substrings of the input. Like we discussed with the StringBuilder in the same function, if we declare this list in the function we will reset the list with each recursion, so we'll pass the list as a parameter instead. Lastly, where we would have printed the output before, we now need to assign the output to a list. If we use a String Array List to hold the results, we can just add the StringBuilder as a string to the list. 

	public static ArrayList<String> AllCombinations(String input, int start, StringBuilder output, ArrayList<String> results){
    	
        for( int i = start; i < input.length(); ++i ){
            output.append(input.charAt(i));
            results.add(output.toString());
            if (i < input.length()) {
            	AllCombinations(input, i + 1, output, results);
            }
            output.setLength(output.length() - 1);
        }
        return results;
    }

Easy Peasy. Good job! Now let's repeat the process for the AllPermutations function:

    public static ArrayList<String> AllPermutations(String permutation, String input, ArrayList<String> output)
    {    
        if(input.length() == 0)
        {
            output.add(permutation);
        }
        else
        {
            for (int i = 0; i < input.length(); i++){    
                StringPermutation(permutation+input.charAt(i), input.substring(0, i)+input.substring(i+1, input.length()), output);
            }
        }
        return output;
    }}

Now, let's try to combine these two functions in one new function that will do both. We don't want to rewrite code, so we will call the functions we already wrote in our new function. The new function will need to:
- Take in a word
- Run the AllCombinations function to get a ArrayList of all possible substrings of the word
- Pull one entry from the AllCombinations ArrayList
- Run the AllPermutations function on the entry
- Add results of AllPermutations to a List
- Repeat until no entries remain in the AllCombinations list
- Return list of all permutations

There are a couple of things to keep in mind as we write up this function. First, AllCombinations will take in an empty ArrayList for it's results. This ArrayList will NOT be empty after we run the AllCombinations function. When AllPermutations needs an empty ArrayList we'll have to create a new one.

Second, if an ArrayList needs to be empty, we had better make sure it stays that way. If we pass an array list that isn't empty we could find ourselves iterating over hundreds of entries. Even worse, the loop may never end if it is always adding entries to what should be an empty list. So we should remember to clear any ArrayList that should be empty after we use it.

Lastly, we need to use unique names for the values we pass to the functions. When creating our functions we used names like input in both functions. That's fine in the definitions, but when we want to use them we can't have the inputs for both functions named input because they need to be differnt values.

With these things in mind, let's write some code!

	public static ArrayList<String> AllWords(String input){
		int start = 0;
		StringBuilder output = new StringBuilder();
		ArrayList<String> results = new ArrayList<String>();
		
		results = AllCombinations(input, start, output, results);
		
		ArrayList<String> permutations = new ArrayList<String>();
		ArrayList<String> empty = new ArrayList<String>();
		
		for (int i = 0; i < results.size(); i++){
			String pinput = results.get(i);
			permutations.addAll(AllPermutations("", pinput, empty));
			empty.clear();
		}
		return permutations;
	}
    
Results for input "ABCD" should look like:

	A, AB, BA, ABC, ACB, BAC, BCA, CAB, CBA, ABCD, ABDC, ACBD, ACDB, ADBC, ADCB, 
    BACD, BADC, BCAD, BCDA, BDAC, BDCA, CABD, CADB, CBAD, CBDA, CDAB, CDBA, DABC, 
    DACB, DBAC, DBCA, DCAB, DCBA, ABD, ADB, BAD, BDA, DAB, DBA, AC, CA, ACD, ADC, 
    CAD, CDA, DAC, DCA, AD, DA, B, BC, CB, BCD, BDC, CBD, CDB, DBC, DCB, BD, DB, C,
    CD, DC, D
    
That's a lot of results for four little letters. Remember, the results are every possible combination, in every possible order from the given input. A large word could easily give hundreds of results. This calls in some questions about if our function is as efficient as it would need to be in practice. Honestly, I don't know. I know it works and it makes sense. In the future I may research some other solutions to this problem and see if I can find something more efficient. 

For now, I'm going to congratulate myself on some coding completed. And you should congratulate yourself, too, for getting this far. We are all one step closer to a word game. Go us!

As usual, don't forget to check back in next week for some more coding fun. We'll get to this game soon, but we have a lot of work to do before we do. Until then,

Thanks for reading and Happy Coding!
