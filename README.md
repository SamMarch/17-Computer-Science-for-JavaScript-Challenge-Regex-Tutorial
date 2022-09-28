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
