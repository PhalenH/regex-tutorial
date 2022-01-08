# Regex Tutorial

This tutorial will help explain how a specific regular expression functions by breaking down each part of the expression and describing what it does.

## Summary

A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input and each component of a regex has a unique responsibility to perform said validation.
In this walkthrough we'll be covering aspects of the Complex Password Strength regex which includes checking for:
1 lowercase letter, 1 uppercase letter, 1 number, 1 special character and be at least 8 characters long

The regex looks like this:
``` /(?=(.*[0-9]))(?=.*[\!@#$%^&*()\\[\]{}\-_+=~`|:;"'<>,./?])(?=.*[a-z])(?=(.*[A-Z]))(?=(.*)).{8,}/ ```

## Table of Contents

- [Anchors](#anchors)
- [Positive Lookahead](#positive-lookahead)
- [Range and Character Classes](#range-and-character-classes)
- [Star and Dot](#star-and-dot)
- [Character Escapes](#character-escapes)
- [Quantifiers](#quantifiers)

- [Bracket Expressions](#bracket-expressions)
- [The OR Operator](#the-or-operator)

## Regex Components

### Positive Lookahead
    - Lookaheads allows to add a condition for “what follows”
    - Lookbehind is similar, but it looks behind. That is, it allows to match a pattern only if there’s something before it.

    - Our example uses only positive lookaheads, and checks for numbers(0-9), letters(a-z upper and lowercase), and special characters

    - How a lookahead is written out: `(?=`


### Ranges and Character Classes
    - Ranges allows you to specify a range of characters by using a hyphen. With a “character class”, also called “character set”, you can tell the regex engine to match only one out of several characters. For our example, it matches a character in the range of numbers 0 through 9, letters a through z lowercase, and letters A through A uppercase.

    - While we don't use it for this password checking, a regex could use [1-9][0-9] to match double digit numbera from 10 to 99.

    - Examples in our regex: `[0-9]` / `[a-z]` / `[A-Z]`


### Star and Dot
    - A star ( `*` ) will match 0 or more of the preceding token
    
    - A dot ( `.` ) matches any character except line breaks
    
    - Combined the dot matches any character, and the star allows the dot to be repeated any number of times, including zero and will prevent any line breaks. So a user will not be able to use "pass word" since it contains a line break
    
    - It is used prior to all character classes in the password regex
    
    - Example in our regex: `.*[0-9]` 


### Character Escapes
d

### Quantifiers
`{8,}`

### Anchors
- The `^` and `$` meta-characters are anchors that fix a regex match to the beginning (^) or ending ($) of a line of text.
The regex we're covering does not use anchors but includes the characters due to the password container "special characters"


### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

## Author

I'm Phalen Hazel, full-stack web developer who is finishing up the last portion of the Upenn Coding Bootcamp. I hope to transition full time into a web development based career
upon completion of the program and couldn't be more excited for what the future holds. If you have any questions, email me at pchaze@yahoo.com and checkout projects I've done both
by myself and with group members on my GitHub profile [here](https://github.com/PhalenH).


WHEN I open the tutorial
THEN I see a descriptive title and introductory paragraph explaining the purpose of the tutorial, a summary describing the regex featured in the tutorial, a table of contents linking to different sections that break down each component of the regex and explain what it does, and a section about the author with a link to the author’s GitHub profile

WHEN I click on the links in the table of contents
THEN I am taken to the corresponding sections of the tutorial

WHEN I read through each section of the tutorial
THEN I find a detailed explanation of what a specific component of the regex does

WHEN I reach the end of the tutorial
THEN I find a section about the author and a link to the author’s GitHub profile
