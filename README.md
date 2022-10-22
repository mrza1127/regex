# Email Regex Tutorial

Regex refers to Regular Expressions, regex is used in many programing languages so developers can find specific combination of characters. Regular Expressions allows a programmer to search  for variations of string matching a specific pattern rather than being limited to a query. Having this in mind, think about a large database with 100,000 users (with name, last name,  email) & you need to find someone by email. 

## Summary

In this tutorial we will learn how use regex(Regular Expression) to match an email. Below you'll see an example of what is used to verify user input is a vaild email address.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Let's get started.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping and Capturing](#grouping-and-capturing)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Conclusion](#conclusion)

## Regex Components

### Anchors

To start off, regular expressions both begin and end with a foward slash "/". In regular expression for matching an email address, we have surrounded our RegEx search with the anchors ^ and $ to identify that the enclosed search pattern should not have any other characters, including spaces, before or after it. Within the foward slash we encounter a caret (^) anchor which identefies the beginning of a string and the dolllar sign ($) identefies as the end of the string. The metacharacter (/b) is used to identify the begining or end of a word.

let's think about this for a second. If you use RegEx to search for /book/ it'll return "book" wherever its located because it does not care about the positioning within the string. If we plug in "$" we get /book$/ and will only find "book" located at the end of the string. If we use /^book/ it won't return any matches because there are no instances that start with "book" in the beginning of a string. Lastly, if we want to only look for the word 'book', we enclose the RegEx search. (/\book\b/).


### Quantifiers

Quantifiers are instances of a character, group, class must be present in the input to find a match.
Below are some exaples of quantifiers:

 Greedy Quantifier | Lazy Quatifier |  Description |
| ----------------- | -------------- | ------------- |
| *                 | *?             | Match zero or more times. |
| +                 | +?             | Match one or more times. |
| ?                 | ??             | Match zero or one time. |
| { n }             | { n }?         | Match exactly n times. |
| { n ,}            | { n ,}?        | Match at least n times. |
| { n , m }         | { n , m }?     | Match from n to m times. |

The email RegEx uses a plus (+) and brace ({....}) qunatifiers, here is an example shown here:
([...]+)@([...]+)\.([...]{2,6}) 

As you can see, the plus (+) in the example above shows to look for a match for the characters specified in the proceeding bracket expression one time. The brace shows how it ranges from 2 to 6 of the characters found in the next bracket expression.


### Grouping and Capturing

In reference to our matching and email with Regex, we will pay attention to the parentheses (...)@(...)\.(...). 
Below is the matching email regular expression:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Parentheses does not affect the results of a search pattern but rather group the items within the parentheses. the entire string is group 0 but each subsequent parenthetical captured group is group 1, group 2, group 3, group 4, etc. catured groups can be reference as needed. 

### Character Classes
A character class you can tell the regex engine to match only one out of several characters. Put the characters you want in the [] brakcets say for example [ae] which can be used to find words like "gray" or "grey" and will not return "graay" or "graey". below is a table with character classes.

| Character Class | Meaning |
| -----------------  | -------------- |
| a-z | Match any letter within the range of lowercase a to lowercase z.                                                               |
| 0-9 | Search any digit which is between the brackets                                                                                 |
| @   | Match literal at signs. Found following the first parenthetical group in our email RegEx.                                      |
| -   | Match literal hyphens.                                                                                                         |
| \d  | Match a digit or a character from 0 to 9                                                                                       |
| _   | Match literal underscores.                                                                                                     |
| \D  | Matches any character that is not a digit                                                                                      |
| \.  | Match literals dot (.). Dots have special functions in regular expression. The backslash (\) is used to escape the character.  |            


### Bracket Expressions

A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions, ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions. A matching list expression specifies a list that matches any single character that is matched by one of the expressions represented in the list. An ordinary character in the list should only match that character, but may match any single character that collates equally with that character.

The character sequences "[.", "[=", and "[:"  should be special inside a bracket expression and are used to delimit collating symbols, equivalence class expressions, and character class expressions.

### Greedy and Lazy Match

What is a greety match?
A greedy match means that the regex engine (the one which tries to find your pattern in the string) matches as many characters as possible. For example, the regex 'a+' will match as many 'a' s as possible in your string 'aaaa' .

What is a lazy match?
Lazy' means match shortest possible string. For example, the greedy a. +l matches 'apple' in 'area' but the lazy a.

head to my [Quantifiers](#quantifiers) section where you'll see a list of greety and lazy quantifiers.

### Boundaries

Boundaries. 
 \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length. there are 3 different positions that qualify as word boundaries:

- Before the first character in the string, if the first character is a word character.
- After the last character in the string, if the last character is a word character.
- Between two characters in the string, where one is a word character and the other is not a word character.

\bApple\b \bWord\b

the \b anchor allows you to search for full words like the examples above.



### Back-references

Back-references match the same text as previously matched by capturing group. Below an example,

<([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>

Suppose you want to match a pair of opening and closing HTML tags as well as the text in between. By making the opeing tag a backreference, we can reuse the same name of the tag for the closing tag section. above shows how to get it done.

### Conclusion
We discussed the following:
- How we used anchors ^ and $ for our begining and end of a string as well as our forward slash begin our regular expression.
- We disccused about greety and lazy qunatifiers, Greety to match as many characters as possible and Lazy as little as possible.
- We talked about grouping and capturing using parentheses format.
- Bracket expressions matching list and non-matching list.
- Boundaries being able to search for words using \b.
- Using backreferences to recall previous code to reuse.

## Author

[Github](https://github.com/ismo1127)
