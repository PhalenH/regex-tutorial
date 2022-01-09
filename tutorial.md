# Complex Password Strength Regex Tutorial

This tutorial will help explain how the Complex Password Strength regular expression functions by breaking down each part of the expression and describing what it does.

## Summary

A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input and each component of a regex has a unique responsibility to perform said validation.
- In this walkthrough we'll be covering aspects of the Complex Password Strength regex which includes checking for:
1 lowercase letter, 1 uppercase letter, 1 number, 1 special character and be at least 8 characters long

The regex looks like this:

- ``` /(?=(.*[0-9]))(?=.*[\!@#$%^&*()\\[\]{}\-_+=~`|:;"'<>,./?])(?=.*[a-z])(?=(.*[A-Z]))(?=(.*)).{8,}/ ```

## Table of Contents
- [Positive Lookahead](#positive-lookahead)
- [Ranges and Character Classes](#ranges-and-character-classes)
- [Star and Dot](#star-and-dot)
- [Character Escapes](#character-escapes)
- [Quantifiers](#quantifiers)
- [Capturing Groups](#capturing-groups)
- [Examples](#examples)
- [Anchors](#anchors)
- [Author](#author)

## Regex Components

### Positive Lookahead
- Lookaheads allows to add a condition for “what follows”. This part of an expression will match for a pattern that are followed by another pattern. Any valid regular expression can be used inside the lookahead. A Lookbehind is similar, but it looks behind. That is, it allows to match a pattern only if there’s something before it.
- Our example uses only positive lookaheads, and checks for numbers (0-9), letters (a-z upper and lowercase), and special characters.
- How a lookahead is written out: `(?=`
- Examples in our regex: `(?=(.*[0-9]))` / ```(?=.*[\!@#$%^&*()\\[\]{}\-_+=~`|:;"'<>,.?])``` / `(?=.*[a-z])` / `(?=(.*[A-Z]))` / `(?=(.*))`

### Ranges and Character Classes
- Ranges allows you to specify a range of characters by using a hyphen. With a “character class”, also called “character set”, you can tell the regex engine to match only one out of several characters. For our example, it matches a character in the range of numbers 0 through 9, letters a through z lowercase, and letters A through A uppercase. Charatcer classes must be within bracket expressions. If there is a carat (`^`) inside a class or range it will exclude the characters that follow the carat (does not occure in this regex).
- While we don't use it for this password checking, a regex could use [1-9][0-9] to match double digit numbera from 10 to 99.
- Examples in our regex: `[0-9]` / `[a-z]` / `[A-Z]`

### Star and Dot
- A star ( `*` ) will match 0 or more of the preceding token (this is also considered a quantifier).   
- A dot ( `.` ) matches any character except line breaks    
- Combined the dot matches any character, and the star allows the dot to be repeated any number of times, including zero and will prevent any line breaks (this combination also referred to as a wildcard). So a user will not be able to use "pass word" since it contains a line break. It is used prior to all character classes in the password regex. It's also preceded by the positive lookahead which will looks at the character set ahead of the `.*` which allows the password regex to check for all the characters withing the set.
- Example in our regex: `.*[0-9]` 

### Character Escapes
- Also referred to as escaped charatcers, these can be used to insert reserved, special, and unicode characters. All escaped characters begin with the \ character. You also escape certain letters that represent common character classes, such as \w for a word character or \s for a space. In this regex it only uses escapes for special characters.
- Examples in our regex:  `\!`  ,  `\-` ,  `\\`  ,  `\]` 

### Quantifiers
- Quantifiers indicate numbers of characters or expressions to match. Since our quantifier has a ( `,` ) after the 8 it means it will match at least that many times instead of exactly 8 which would be the case if it was written without the comma. In this regex it will match at least 8 occurrences of the preceding character which is a dot( `.` ), so any character except for line breaks.
- Example in our regex: `.{8,}`

### Capturing Groups
- Capturing Groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. It allows to get a part of the match as a separate item in the result array. This allows you to apply a quantifier to the entire group.
- Example in our regex: `(.*[0-9])` / `(.*[A-Z])` / `(.*)`

## Examples
- Will work
    - Thiswill1!
    - 12345aA!
    - oneTwo*0
- Will not ( Not enough characters or doesn't include a capital & lowercase letter, special character, or number )
    - Eight5^ 
    - 1234567*
    - passWord1

### Anchors
(bonus explanation)
- The `^` and `$` meta-characters are anchors that fix a regex match to the beginning (^) or ending ($) of a line of text.
- The regex we're covering does not use anchors but includes the characters due to the password container "special characters"

## Author

- I'm Phalen Hazel, full-stack web developer who is finishing up the last portion of the Upenn Coding Bootcamp. I hope to transition full time into a web development based career
upon completion of the program and couldn't be more excited for what the future holds. 
- If you have any questions, email me at pchaze@yahoo.com and checkout projects I've done both
by myself and with group members on my GitHub profile [here](https://github.com/PhalenH).