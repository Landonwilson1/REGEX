# REGEX Tutorial: Matching HEX

The hexadecimal number system, sometimes just called HEX, is a number system that uses 16 unique symbols to represent a particular value. These symbols are 0-9 and a-f.
 
One of the many cases of the hexadecimal number system are hex color codes. These color codes represent a color in RBG format. For example: 

```
BLUE #e2f1fb
GREEN #00ff00
AQUA #00ffff
```
 
Today we will be focusing on explaining the details on how a REGEX(regular expression) can match a HEX value. Below are detailed explanations on how regex operates with this case.
 
## Summary
 
REGEX expressions can be used for many different purposes. From validating emails to password security. This document will be focusing on an expression that is used to match HEX values.
 
```/^#?([a-f0-9]{6}|[a-f0-9]{3})$/```
 
## Table of Contents
 
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
 
## Regex Components
 
### Anchors
 
In regular expressions, anchors are used to check if the matching symbol is the starting symbol or the ending symbol of the input string. There are only two types of anchors. The first is the caret ```^```. This will match characters at the start of the string as well as after each line break.. The second type ```$``` matches at the end of the string and before every line break. 
 
In our expression, both anchors are being used.
 
```/^#?([a-f0-9]{6}|[a-f0-9]{3})$/```
 
These anchors are being used together to make sure the start of the string is matched before the end of the string is.

 
### Quantifiers
 
Quantifiers decide how many instances of a possible character or character class must be in the input of the regex. There are multiple quantifiers in regex; however, our expression only uses two. The ```?``` and the ```{}``` quantifiers.
 
```/^#?([a-f0-9]{6}|[a-f0-9]{3})$/```
 
 
The ```?``` quantifier matches the preceding element zero or 1 times. Since the preceding element is ```?```(```#```)?. The input must match with a # or not. 
 
The second quantifier, ```{}```, is used twice in the regex.
 
/^#?([a-f0-9]```{6}```|[a-f0-9]```{3}```)$/
 
 
This numeric value inside the curly brackets must match the number of times the instance occurs. For example, if the regular expression is ```{3}``` it will have to match any string that has 3 consecutive digits such as 123 or 111.
 

 
### OR Operator
 
In our expression there is one group separated by an OR operator ```|```. Our group is: 
 
```([a-f0-9]{6}|[a-f0-9]{3})```
 
The first expression ```[a-f0-9]{6}``` and the second ```[a-f0-9]{3}```. The OR operator ```|``` will demonstrate that our regex will match either one of those two expressions. For example: regex was being used for email validation. The OR operator in that expression would allow many top-level email domains to match. I.e. ```.com.net.org.```
 
### Character Classes
 
Character classes, also known as a character set, are ways to match only one out of several characters. A character class will match any character inside of brackets. For example: ```[ae]``` will match any ???a??? or ???e???. This could be used with ```gr[ae]y``` to match either grey or gray. 
 
Inside of our expression, we have ```[a-f0-9]``` repeated twice. The class will match two ranges, any letter from a-f and any number from 0-9. 
 
### Flags
 
Flags can be used in a regex to modify a search. There are only six flags in JavaScript (i,g,s,m,y,u). Each flag serves a different purpose in the regex search behavior. There are no flags in our HEX value expression.
Listed below is how the flags operate. 
 
```Flags

i             Makes the expression search case-insensitively.

g             Makes the expression search for all occurences.

s             Makes the wild character . match newlines as well.

m             Makes the boundary characters ^ and $ match the beginning and ending of every
              single line instead of the beginning and ending of the whole string.

y             Makes the expression start its searching from the index indicated in its lastIndex property.

u             Makes the expression assume individual characters as code points, not code units,
              and thus match 32-bit characters as well.
```
 
 
 
### Grouping and Capturing
 
Parentheses are used for grouping and capturing. Placing an expression inside of parentheses allows that part of the expression to be grouped together. This makes it easy to apply a quantifier to the group or to restrict part of the regex.
 
In our expression we have one big group separated by an OR operator. 
 
```([a-f0-9]{6}|[a-f0-9]{3})```
 
  
This grouping works the entire expression inside of the parentheses. This is useful when extracting information using Javascript. 

 
### Bracket Expressions
 
A bracket expression in regex will match any specific pattern of character in a string. Characters can be alphabetic, numeric, special, symbols, etc.. The ```-```` is used to set the range of characters. In our regex we have one bracket expression. 
 
```[a-f0-9]```
 
A range is defined from any letter from a-f(lowercase) and a number 0-9. 
 
### Greedy and Lazy Match
 
A greedy match means that it will be the longest possible string. Lazy means that it will match the shortest possible string. Greedy matches are needed in JavaScript to match as many occurances of a particular pattern as possible. For example our regex expression uses ```[a-f0-9]{6}```. This will match as many as 6 occurrences making it a greedy match.
 
### Boundaries
 
Boundaries are used with the metacharacter ```\b```. It matches at a position that is called a ???word boundary???. There are multiple instances of using a boundary. Before the first character in the string, after the last character in the string, and between the two characters in a string. There are no boundaries in our regex.
 
### Back-references
 
Back-referneces match the same text previously matched by a capturing group. For example: ```([a-c])\1\1``` matche ```aaa, bbb,and ccc```. The back-reference ```\1``` refers to the first capturing group. ```\1``` matches the same text that was matched by the first capturing group. 
 
### Look-ahead and Look-behind
 
The look-ahead asserts that what immediately precedes the current position is a lowercase letter. And the look-behind asserts that what immediately follows the current position is an uppercase letter.
 
 
## Author
 
Landon Wilson </br>
A full-stack web developer working to complete UCF???s coding bootcamp. </br>
To contact me please visit my github profile [github.com/Landonwilson1](https://github.com/Landonwilson1)
