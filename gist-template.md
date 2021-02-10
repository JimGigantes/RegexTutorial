# Title (replace with your title)

Regex Tutorial 

## Summary

This is a general tutorial of regualr expression in JS (Regex). Regex is used to search through a string of text. It is more or less a set of instructions for the machine to fine selected groups of text from a larger string.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
^ (carrot): this enables you to match a chatracter at the beginning of the line. 
    Example /^T/g would match only the first T of a string. It doesnt matter if there are multiple line brakes or multiple T's starting multiple sentences in a single string. It would only match the first T of the first sentence if there is one. If not, it wouldnt match anything in the entire string. /^T/m would enable you to match multiple 'T's in the string if in the case more than one line starts with a 'T'

$ (dollar sign): this is something that we would use in order to match the last character of the string. 
    Example: /\.$/g would match the '.' at the end of a string. In the sentence, "This cat is cool." it would match the final. Even if there are multiple lines. If in the case you added multi line it would match every period at the end of every line. 

\A	The match must occur at the beginning of the string only (no multiline support). 
    Example /\AT/g would match only the first T of a string. It doesnt matter if there are multiple line brakes or multiple T's starting multiple sentences in a single string.


\Z	The match must occur at the end of the string, or before \n at the end of the string. 

\z	The match must occur at the end of the string only. 

\G	The match must start at the position where the previous match ended. 

\b	The match must occur on a word boundary. 

\B	The match must not occur on a word boundary.

\ (Backslash): This has a special function where it can cancel the special characters. So, if in the case you want to search for punctuation in a string, or something similar, this would enable you to stop the special functions within regex.
    Example: /\./g would enable you to search for all of the periods in a string of text. You could also be crafty and try /.\./g this would match all of the periods in a string of text and the character that comes before it. 


### Quantifiers

    Quantifiers are used to help define instances or multiples of a search term that the user is trying to find. In the case that you are looking for single instances of a character or if a character is optional. You may want to include a quantifier to indicate exactly what you are looking for. 

+ (Plus sign): match the string or more than one of the search terms.
    Example: /e+/g would find all of the e's in a string and if there are double e's anywhere in the string it will match all of them.

? (Question Mark): This would make a certain portion of the search term optional. 
    Example: /ea?/g would indicate that we are looking for all instances of 'e' but the 'a' is optional.

* (star): Indicates that you are looking for the character (as many instances of the character are acceptable) but it is also optional.
    Example: /ea*/g would indicate that you are looking for 'e' and that instances of 'ea' are optional as are instances of repeating 'a's after the 'e'. Example "eaa" or "eaaaaa" are all acceptable.

. (period): The period indicates that you are looking to match anything before or after the '.' except for a new line. 
    Example: /.e/g would match the "se" in "sea". /e./ would match the "ea" in "eat". /ea../ can’t match a new line though so if you say "This is where I eat." followed by a new line it will not match. 

{} (curly braces): This would enable you to start specifying how many characters you are looking for in the search term
    Example: /\w{4}/g would match every word that is 4 characters or more. If you were to add a ,5 it works as a max so /\w{4,5}/g would return every word that is 4-5 characters long.

\w (backslash uppercase W): This would match anything that is not a word in an array.
    Example: /\W/g would return a match for every space, punctuation, and everything else that is not a word in a string.


\s (backslash lowercase s) :This would match all white spaces
    Example: /\s/g would match every blank space in a string.

\S (backslash uppercase S) : This would match everything that is not a white space 
    Example: /\S/g would match everything that is not a space in a string.


### Grouping Constructs

    Generally you can create lengths of expressions in order to find very specific matches. Your searchterms can become quite expansive. and so here are a couple of steps and examples of how you might go about this.

() (grouping parenthises): anything inside of the parentises are going to be in their own group and they only act upon themselves.
    Example: /(c|C)at/g would return all instances of the work Cat or cat within a string. If you used /c|Cat/g it would return any c or the work Cat.


    Look aheads and look Behinds
    Look Behinds: (?<=) this expression is saying that we are looking for anything that is behind our search term and that it must be positive. Being positive means that it must match. 
        Example: /(?<=[tT]he)./g would return the charater (spaces included) that follows the work 'The' Or 'the' in a string.

    You can make this negative by changing the '=' to a '!'. This would return a match for everything in the sentence that is not the character or space after the word 'the' or 'The' in the string.

    Look Ahead: This is very similar

### Bracket Expressions
    [] (Square Brackets): These help to provide a ranges, it also helps you to specify particular characters that you might be looking for before or after a line of text.
    Example: /[fc]at/g would match for all of the 'fat' and 'cat' instances in a string. Or if you would like to match for any of the characters from A-Z you can do that. /[a-z]at/g would match every instance of a character followed by at so 'pat', 'bat', 'vat' would all be matched. /[a-zA-Z]at/ also works to identify all instances where lowercase or uppercase. You can also use shorter ranges (c-t, B-Q, whatever). You can also place meta characters like '.'

### Character Classes

Generally this is stuff that appears between []

    You can place "abc" inside of [] and the machine would try to match an a, b, or c within a string. 

    Example: /l[yi]nk/g would match either Link or Lynk in a string

    you can also run numbers [0-9] which can also be denoted as \d

    You can use this to verify Phone numbers. 

    Example: \d\d\d-



    
\d (Digits): Numbers 0-9

### The OR Operator

(|) (grouping parenthises with a vertical pipe): anything inside of the parentises are going to be in their own group and they only act upon themselves.
    Example: /(c|C)at/g would return all instances of the work Cat or cat within a string. If you used /c|Cat/g it would return any c or the work Cat.

### Flags
Flags are used to provide more context about the string that you are looking for.

g (Global): Looking for all instances of the text throughout the string. If we do not include 'G' we will only find the first match that we find. 
i (Case Insensitive): It ignores the capitalization when trying to find matches.
m (Multi Line): This enables you to look to multiple different lines of the string, to see if there are matches in different parts of the string.  

u (unicode)
y (sticky): this tries to match the lastIndex property. So if you have the following code 

    var reg = /t/y
        reg.lastIndex = 6
    "I went to the store earlier.".match(reg); It would return True. 
    
    What happens here is that it is is trying to match a particular part starting at a particular character (defined by lastIndex). There are a few things to remember. After it returns true. It then increments. So since it returned true this last time it will increment to 7. If it ever returns null, it will go back to a value of 0. 


### Character Escapes

\ (Backslash): you can use  the backslash to help escape using the Regex function of a character. For instance if you are looking to match a file type you might try /.txt/ but that may not work if there is something else other than a '.' in the name of the file. So using the back slash this way /\.txt/ removes the regex function associated with the '.' which of course would normally match whatever comes before the txt in this example.


## Author

The author of this assignment was James Gigantes. I'm a Scrum Master who is studying to become a part time coder. Here is my GitHub https://github.com/JimGigantes
