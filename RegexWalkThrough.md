# Regular Expressions Walk Through/Tutorial!

Hello and welcome to a tutorial walk through on the topic of Regular Expressions!

## Summary

For this Regular Expressions walk through, we will cover how you can use regular expressions to validate a valid email input, or throw flags when its not valid. We will be using RegEx to ensure that the email provided is a valid email. Once you have finish this walk through, my hope is for anyone walking through this process will have a much better understanding of the benefits to using regular expressions.

this is our starting point for a regular expression:

```js
/^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})$/
```
Don't worry its not has bad as it looks trust me!

This intro will cover the basics of regular expressions to "validate/confirm"  or use RegEx to "extract/select" information from a string that matches the pattern you create, "replace/substitute" this from a string with other strings, and "split" pieces of the pattern you select to transition/move the string information to an array of pieces of that same string!

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

There are a multitude of RegEx components at our disposal when using regular expressions. The main components we use in RegEx are "Single Characters", "Wildcards", "Brackets Expressions", "Escaped Characters", "Groups", and "Quantifiers". The following sections will outline everything you need to be aware of.

When writing general expressions, we don't want any spaces in our expression what so ever. And we want to begin and end our expression with a "/". In the example we will be using, we'll be using Javascript.

### Anchors

The purpose of Anchors are to tell RegEx what you're trying to do with a specified component. We can use this character  "^" to denoted the beginning of our RegEx and "$" to denote the end. 

For this example using our email, we want to start our RegEx with a specific component. Let's try this with the email: fakeEmail123@email.com. Here we can see that we have "fakeEmail123", then "@", then "gmail", then ".", and finally, "com". So, we want to start the expression with "fakeEmail123" and we want to end it with "com".

 start as something like this:

```js
/^
```

end with something like this:

```js
$/
```

Altho not as popular, you can also use /b and /B. /b will allow you to see if the user's input has something specific at the start/end of string. 

### Character Classes

Character classes allow us to specify the characters from a user's response. 

you can find an abundance of character classes, including: "[xyz]" which will match any character specified in the set, also "[^abc]" and that will match any character that is not specified in the set, "[a-z]" which will match any character that is specified in the range provided in the set, "." allows us to match any character (besides line-breaks), [\s\S] which allows us to match anything (including line-breaks), "\w" or "\W" which respectively allow us to match every word or everything that isn't a word, and "/d" or "/D" which respectively allow us to match every digit or everything that isn't a digit from the user;s input. 

### Bracket Expressions

Now for Bracket expressions, they allow us to match any characters or ranges of characters. We can write bracket expressions to include the following: lowercase letters, uppercase letters, numbers, and special characters.

In the beginning of our fakeEmail example, remember that we want to match "fakeEmail123" after the "^" anchor. We can do this with a character set by allowing all letters and numbers in our brackets. 

Our updated beginning now looks like this:

```js
/^[a-zA-Z0-9_]
```

not quite done just yet, but now our users can enter emails that start with any character such as: lowercase letters "a-z", capital letters "A-Z", numbers "0-9", and underscores also!

In the middle part of our example, between the "@" and the "." is the email provider. That can be literally anything, just like the beginning can. So we would write it the same way but not with the carrot this time "^" because this part will not be at the beginning.

```js
[a-zA-Z0-9_]
```

And now finally, our ending will be something like ".com", ".io", or ".net", now we are worried about allowing alphabetic characters for the user's email submission. Now we can bring in the "$" to signify the end.

The ending of our expression will look like the following:

```js
[a-zA-Z]$/
```

### Character Escapes

Character Escapes, allows "escape" keywords and special characters in RegEx to be used in our expression to match the character they represent on the users keyboard. RegEx has tons of escape characters but the most commonly used is the "\" which, when it comes before something, let's us access the character as a pattern match parameter in regular expressions.

such as , when we want to allow users to include a "-" and a "." in the first part of their email submission. Thus, we need to use the escape character "\" to make those matching parameters available.

updated expression beginning:

```js
/^[a-zA-Z0-9_\-\.]
```

updated expression beginning:

```js
[a-zA-Z0-9_\-\.]
```

Ending will look the same:

```js
[a-zA-Z]$/
```

### Quantifiers

Quantifiers are the pieces of RegEx that allow us to specify the amount of a component we are using to validate a user's input. "+" means 1 or more of the "thing" that come before the plus sign, "*" means 0 or more, "?" means that the "thing" is optional, and {min, max} allows you to target the min and max quantity of something that we are expecting.

In the example, the way our expression stands it will only acknowledge the first letter in the example email. However we want to allow the user to add how ever many of the allowed characters as they want to before the "@" in "FakeEmail123@email.com". To do this, we just need to add a "+" to that part of the expression!

Updated expression beginning:

```js
/^[a-zA-Z0-9_\-\.]+
```

Updated expression middle:

```js
[a-zA-Z0-9_\-\.]+
```

The ending expression will now change. We need to understand that endings of emails end in 2, 3, 4, or 5 characters, so we require a "{min, max}" range for that portion's character length:

```js
[a-zA-Z]{2,5}$/
```

### Grouping Constructs

Grouping Constructs allow us to "group" parts of the total expression. This gives us the power to group multiple components to match what ever it is we want that meets that grouped construct. To group a section of an expression to be evaluated as an individual piece of the expression, we use "(xyz)". 

In the example, we have three separate pieces that need to connect and make validation decisions based on each piece we've created. Thats done by putting them into their own group using grouping constructs. 

expression beginning:

```js
/^([a-zA-Z0-9_\-\.]+)
```

expression middle:

```js
([a-zA-Z0-9_\-\.]+)
```

 ending expression:

```js
([a-zA-Z]{2,5})$/
```

Now that  we already know how to escape special characters with "/", we can now use "." to match with "@" which is not a reserved character, now piece our entire regular expression together as provided below: 

```js
/^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})$/
```

### The OR Operator

OR Operator provides the ability to create a logical OR operation to say that we are expecting one thing OR another in our regular expression. how to start using the logical OR.... we simply use "|". We can also link together as many logical OR operators we wish.

 We could allow the user to enter a phone number instead of an email. Assume we have a very user-choice driven application that allows this type of input. To implement this, we need to create the RegEx that can validate a proper phone number. 

here is a basic RegEx that can match something like "123-456-7890". To do this, we first need to start with a "^" and then allow any number one through nine with "[1-9]" or "/d" for the first three digit "{3}".

Next, we'll do the same thing for the middle three numbers without the "^". Lastly, we'll do the same with four digits to end the expression with a "$". Next we have to connect these expression pieces together, by using dashes by escaping it's reserved character nature with "/-"!

Our phone number:

```js
/^\d{3}-\d{3}-\d{4}$/
```

To put this all together, we wrap each of our final expressions in grouping construct. Next we place the OR operator between them to create one massive regular expression! User will have a choice of entering a valid email or a valid phone number of the format "XXX-XXX-XXXX".

Final regular expression:

```js
/(^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})$)|(^\d{3}-\d{3}-\d{4}$)/
```

### Flags
LASTLY! Congratulations on making it this far!
Our last topic will cover "Flags".
These are special characters that we can add to the end of an expression after the "/" to denote how the RegEx as a whole should be viewed. Here's the most common: "i" communicates with the RegEx to not be Lower or Upper Case-sensitive and "g" lets you search every matching result of the regular expression matches, and "m" which allows the "^" and "$" to refer to the start and end of a line instead of a string.

There is no special need in our example to use any flag in particular, but they will become useful to you throughout your endeavors in the coding world!
I hope this was helpfully and best of luck to you! 

## Author

Walk Through Tutorial Created By Chris Kennard

GitHub: [chris79kennard](https://github.com/chris79kennard)
