---
published: false
tags: strings challenges regex exercises walkthrough
---
Regular Expressions are a pain. Truly, a royal pain. They aren’t easily readable, they can go on for what seems like eternity, and the more we add the easier it is to get confused. There are dozens of cheat sheets on the internet because almost no one will ever remember how to write RegEx off the top of their head. There are apps designed to test and even generate RegEx for us. From what I’ve been able to gather, the whole IT community hates regulation expressions. 

I actually *don’t* hate regular expressions. Yes, RegEx can be a pain. Yes, RegEx can be confusing. No, I cannot write regular expressions off the top of my head. All of that just adds up to a challenge and I feel a great satisfaction when I beat it. When I write an expression and it *works*, man, I love it. Which is good, because I can’t make the game I have written up in the [Strings and Things Challenge]( https://sjcswank.github.io/2019/02/06/Stings-and-Things/) without them.

< more>

Well, actually, I’m sure there is a way to create this game without ever having to use regular expressions. There’s always another way to do it in programming. This just happens to be the way that I figured out, the way that makes sense to me. If we think of another way to get the same or similar result, please let me know because, as I said above, people really tend to hate RegEx. This challenge is supposed to be fun, not torture.

**But What *Is* RegEx?**

Good question. Regular Expressions are combinations of characters that represent patterns in strings. We use a set of predefined characters almost like a code- ^ says to look at the characters at the beginning of the text, $ the end, [A-C] represents letter A, B, and/or C. Every character we put into a Regular Expression has a meaning and defines a rule for the matching strings. 

RegEx is kind of its own language, used with nearly every programming language. Some languages use their own “flavor” of RegEx, but it remains mostly unchanged most of the time.  There are many uses, such as searching for specific words in a text or validating user input. 

**The Cheats**

There really are dozens of different cheat sheets and other resources to help with creating and testing regular expressions. Some are visual, some textual, and all are designed to make it easier to remember, understand, and use the rules of RegEx. Here are some of my favorites, in no particular order:
- [This run down of RegEx rules and usage]( https://www.regular-expressions.info/quickstart.html)
- [This website that lets you edit and test RegEx in real time]( https://regexr.com/)
- [This collection of quick reference tables]( https://www.rexegg.com/regex-quickstart.html) 
- [This MDN article]( https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
- [This video explaining RegEx in some detail]( https://www.wetube.com/watch?v=sa-TUpSx1JA)

**The Regular Part**

Regular Expressions are all formed from the same set of predefined characters and character combinations. These characters have the same meanings from use to use. The characters we use, in what orders, will determine what pattern(s) our RegEx will match. Once put together, those characters will always match the same pattern. They are continuously the same, regular.

There are a few basic ideas, or parts, of regular expressions. Anchors, character classes, flags, grouping, and quantifiers are some of the most basic. There are others, and someone else might say that these are not the key parts of RegEx, but this is how I understand it. 

***Anchors***

Anchors are pretty straight forward- they determine where in the string the pattern should be found. Like an anchor for a boat, the characters attached to the anchor will stay in the place the anchor holds. There are only two anchors: “^” for at the beginning and “$” for at the end. Characters, or groups of characters, preceded by “^” will only be matched if at the beginning of the string. Conversely, characters followed by “$” will only be matched at the end. 

	^The matches strings that start with “The” only
	End$ matches strings that end with “End” only
	^The End$ matches strings that begin with “The” AND end with “End” only

***Character Classes***

I'm not talking about Dungeons and Dragons here. With these character classes we can look for generic characters, such as digits only. With classes we don’t have to define what characters exactly we are looking for like the above example. Instead we can just match the type of character we want. There are 4 character classes we can use. “\d” matches only digits, “\w” matches alphanumeric and underscore characters, “\s” matches only white space and “.” matches any letter.

	^\d matches strings that begin with a digit
	\w$ matches strings that end with a letter, digit, or underscore
	\s$ matches strings that end with a space, tabs, or line break
	^. Matches strings that begin with any character including white spaces
    
These character classes can be used to match *not* the class as well. By capitalizing to “\D” we are saying match any character *not* a digit. The same for “\W” and “\S”.

	 ^\D matches strings that *do not* begin with a digit
	\W$ matches strings that *do not* end with a letter, digit, or underscore
	\S$ matches strings that *do not* end with a space, tabs, or line break

***Flags***

Flags are an important element to regular expressions, they determine how characters will be looked for in the text or string. There are three flags- global, multi-line, and case-insensitive. Global means that the search should continue from the end of each match instead of beginning again at the start of the string. Multi-line says "^" and "&" apply to the beginning and end of a line rather than the whole string. Usually, RegEx matches exact case. Matching “AbC” is different than matching “aBc”. Case-insensitive means, well, what it sounds like- “AbC” and “aBc” both match when this flag is used.

/abc/g does not return after the first match of “abc”

^/abc/m ^ and $ will match the start and end of a line, for example

	“abc def
	ghi abc”

would match “abc” in the first line but not the second, because in the second line “abc” is not at the beginning of the line. 

i makes the whole expression case-insensitive (for instance /aBc/i would match AbC)

***Groupings***

When searching for multiple characters in a row, we would need to group those characters together as one search. Rather than searching for a string with “A” in it, and then a string with “b”, we want to find a string with “Ab”. Groupings are denoted by “( )” around the group we are looking for. “A(bc)” would search for a string that has “A” followed by exactly “bc”. Like with classes, we can reverse this effect, this time by adding “?:” to the beginning of the grouping. Conversely, if we want to locate just one of a group of characters we surround the group with “[ ]”. So, A[bc] would find matches of Ab or Ac but not Abc.

	A(bc) matches strings containing A followed by bc only
	A(?:bc) matches strings that contain A *not* followed by bc only
	A[bc] matches Ab *or* Ac but *not* Abc

***Quantifiers***

These characters set how many of each match should be made in the same string. There are several ways to set this rule in our expression. “\*” after a character denotes any number of the character (zero or more matches), while “+” is one or more, and “?” is only zero or one match. Rather than starting at zero or one match, you can define the number of matches you want to see. {5} defines five or more matches. You can even be more exact and set the fewest and most matches you want to see. {2,6} would match two to six repeats of the character to make a match. These same quantifiers can be used after groupings as well. A(bc)* would match a string starting with A followed by zero or more repeats of “bc”.

	abc* matches ab followed by any number of c
	a(bc)+ matches a followed by one or more bc
	abc? matches ab followed by zero or one c
	abc{2} matches ab followed by two or more c
	a[bc]{2,4} matches a followed by two, three or four “b” or “c”

**Full Example**

We can put together any number of the above elements to create complex regular expressions. For the game we will be creating, we have some rules that define a valid word. I gave the requirements that the word must contain a vowel and have only alpha characters.Our RegEx will need to use groupings and quantifiers at the least. 

Let’s build the expression one step at a time. We’ll start with the easiest element- grouping any number of letters only: [a-z]\*. Now we can add that the word must have at least one vowel: [aeiouy]+[a-z]\*. Word’s don’t just start with at least one vowel and end with any number of letters. They might start with any number of letters as well: [a-z]\*[aeiouy]+[a-z]\* Lastly, words might be in upper or lower case letters. Right now we only match to lower case letters. Let’s fix that: [a-zA-Z]\*[aeiouyAEIOUY]+[a-zA-Z]\*.

And we’re done! Later we’ll use this RegEx in our game to find and verify valid words. We might decide to add more constraints to our expressions at a later date. For example, this expression will match a word of any length as long as it has at least one vowel. That could be “a” or “ghrhfajfjfhghjd”. We might want to change that at some point. For right now, we’ve met the minimum requirements for our little game, so I’ll leave it be.

More solutions to the [Strings and Things Challenge]( https://sjcswank.github.io/2019/02/06/Stings-and-Things/) are to come, so don’t forget to check back in next week. And if you figure out a different way to solve the challenge please let me know! Until then

Thanks for reading, and Happy Coding!
