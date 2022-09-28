# Challenge 17 Regular Expressions Tutorial

The purpose of this gist is to explain what a regular expression is and provide a step-by-step tutorial how to use them. Regular Expressions (Regex) is often used when a user is trying to match a certain character combination within a string. Regex is a useful tool for pulling out information from a body of code, as well as for validation. For example, this guide will follow an example code snippet that can be used to matched to an email. This tutorial will explain the different components of regular expressions.

## Summary

The following snippet of code will be used throughout this tutorial to give specific examples on how the different components of regex can be used. The following code snippet can be used for matching against emails. A common use for this code is for validation, to make sure that an email follows the correct format.

Matching Email-

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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

The anchor is a term which defines the start and end of the expression.
In the matching email code below,

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`,

the anchors are the `^` and the `$`. This code is specifically saying that we are looking for something that starts with

`^([a-z0-9_\.-]+)`

notice this missing `/`. Don't worry about everything inside the parentheses just yet, as we we will define what they are later in this tutorial. So for now, what we know is that the anchors are the start and end of a string, which means that if we are to find a match it has follow those guidelines. It also has to end with,

`.([a-z\.]{2,6})$`.

So, it must start and end with the given parameters within the code. If it does not, then it is not a match.

### Quantifiers

Quantifiers are used to determine how many occurences that a specific character or group of characters must to be present in order to have a correct match. For example, if we used the following code in our expression, `xyz+`, then this will attempt to match any string of `xy` followed by at least one `z`. Now lets take a look at our code for matching the email below:

`([a-z0-9_\.-]+)`

As we can see, this will match against any string that contains `a-z`, `0-9`, `_\`, `.`, or `-`. The quantifier `+` is there to show us that the string has to contain at least one of these in order to match correctly.

### OR Operator

The 'OR' Operator is not present in our example code for matching against an email, so for now, in order to talk about the OR Operator, we will take a look at the following code for matching against a hex code:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

What we see here, is an expression for matching a hex code that uses the OR Operator.
What this operator does is look for a matching string where it starts with a `#` first followed by one of the following:

`[a-f0-9]{6}` this will match a 6 character long string which contains a combination of `a-f` letters and `0-9` numbers.

`|` this is the OR Operator

`[a-f0-9]{3}` this will match a 3 character long string that contains a combination of `a-f` letters and `0-9` numbers.

Notice both of the above examples are referencing the same character class `[a-f0-9]`. This is because the OR Operator is looking for a match that starts with a `#` and then either a 6 character long string or a 3 character long string. It does not matter which one it is, as long as it starts with a `#` and then either a 6 character long string or a 3 character long string.

### Character Classes

Character classes are used to match a single character out of a group of characters. For example, if we wanted to match against a string that contains either a `b` or a `c`, we would use the following code:

`[bc]`

However, `/d` is a special character class that matches any digit. So, if we wanted to match against a string that contains a digit, we would use the following code:

`[\d]`

In our example code for mathching against an email, we see `/d` is present and is located after the `@` symbol. This ensures that a letter or number is present after the `@` symbol. This is because the `@` symbol is a special character that is used to separate the username from the domain name. So, if we were to use the following code:

`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

and we were to use the following email:

`sammy.march@hotmail.com`

then we would get a match because the `@` symbol is present and is followed by a letter or number. However, if we were to use the following email:

`sammy.march@.com`

then we would not get a match because the `@` symbol is present, but it is not followed by a letter or number.

### Flags

A flag is not used in the matching email code in this tutorial. A regular expression typically looks like this:

`/pattern/flags`

Where the slashes denote where the regular expresssion starts and ends. A flag can be used after the slash to provide more guidelines for matching. The flags are:

- `g` which stands for "global" which will allow for matching all the instances within a string that follow the matching guidelines set in the regular expression.
- `m` which stands for "multiline" which will search line by line rather than searching through a string as a whole.
- `i` which stands for "insensitive" will make the regular expression case-insensitive, so capitals and lower-case letters will not deture the matching.

### Grouping and Capturing

Grouping and capturing is used to match a group of characters and then store them for later use. For example, if we wanted to match against a string that contains a `b` followed by a `c` and then store the `b` and the `c` for later use, we would use the following code:

`([bc])`

This will match against a string that contains a `b` or a `c` and then store the `b` or the `c` for later use. In our example code for matching against an email, we see the following code:

`([a-z0-9_\.-]+)` and `([\da-z\.-]+)` and `([a-z\.]{2,6})`

These are all examples of grouping and capturing. The first one is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The second one is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The third one is matching against a string that contains a combination of `a-z` and `.` and then storing the string for later use.

### Bracket Expressions

Bracket expressions are used to match a single character out of a group of characters. For example, if we wanted to match against a string that contains either a `b` or a `c`, we would use the following code:

`[bc]`

However, `/d` is a special character class that matches any digit. So, if we wanted to match against a string that contains a digit, we would use the following code:

`[\d]`

In our example code for mathching against an email, we see `/d` is present and is located after the `@` symbol. This ensures that a letter or number is present after the `@` symbol. This is because the `@` symbol is a special character that is used to separate the username from the domain name.

### Greedy and Lazy Match

In the given code for matching an email, there isn't a greedy or lazy match included.

### Boundaries

If in a string, we are looking for for specific words. Boundaries are not used in the given matching an email code.

### Back-references

Back-references are used to match a string that is the same as a previous match. For example, if we wanted to match against a string that contains the same word twice, we would use the following code:

`(\w+)\s+\1`

This will match against a string that contains a word followed by a space and then the same word again. In our example code for matching against an email, we see the following code:

`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

This is an example of a back-reference. The first back-reference is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The second back-reference is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The third back-reference is matching against a string that contains a combination of `a-z` and `.` and then storing the string for later use.

Back-references are not included in the given code.

### Look-ahead and Look-behind

Look-ahead and look-behind are used to match a string that is followed by another string. For example, if we wanted to match against a string that contains a `b` and then is followed by a `c`, we would use the following code:

`(?=bc)`.

This will match against a string that contains a `b` and then is followed by a `c`. In our example code for matching against an email, we see the following code:

`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

This is an example of a look-ahead. The first look-ahead is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The second look-ahead is matching against a string that contains a combination of `a-z`, `0-9`, `_\`, `.`, or `-` and then storing the string for later use. The third look-ahead is matching against a string that contains a combination of `a-z` and `.` and then storing the string for later use.

Look-ahead and look-behind are not included in the given code.

## Author

This tutorial was created by Sam March.

Conatct Sam:

[GitHub](https://github.com/SamMarch)

[Email](marchsam1988@gmail.com)
