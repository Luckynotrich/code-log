1.  [How to convert UUID to String in vanilla javascript?](https://www.cloudhadoop.com/convert-uuid-string#how-to-convert-uuid-to-string-in-vanilla-javascript)
2.  [How to convert String to UUID in vanilla javascript?](https://www.cloudhadoop.com/convert-uuid-string#how-to-convert-string-to-uuid-in-vanilla-javascript)
3.  [Conclusion](https://www.cloudhadoop.com/convert-uuid-string#conclusion)

Sometimes, We need to convert UUID to string and string to UUID in dealing with Database’s unique identifier.

UUID is a Universal unique identifier that represents a unique string based on version 1,2,3,4,5.

UUID is a group of 32 hexadecimal strings with a format of 8-4-4-4-12 characters.

You can read more at [javascript uuid](https://www.cloudhadoop.com/javascript-uuid-tutorial)

This tutorial explains multiple ways to Convert UUID to String and String to UUID

![Ezoic](https://go.ezodn.com/utilcave_com/ezoicbwa.png "ezoic")

## How to convert UUID to String in vanilla javascript?

UUID object has a fromString method which returns the string version. Call the toString method to return the string from a given UUID

here is an examples

It works on all browsers in and simple way.

## How to convert String to UUID in vanilla javascript?

There is no direct way to convert a string to UUID.

Multiple ways we can convert string to uuid in plain javascript

![Ezoic](https://go.ezodn.com/utilcave_com/ezoicbwa.png "ezoic")

-   Using regular expressions
    
-   Create a Regular Expression that matches a string of acceptable characters and replaces the character at 8,12,16,18
    
    Replace the string character at Position with a hyphen.
    

8336b1c6-59e7-4ac7-a0f6-0a80a38ef6a6

-   Another way using the slice string function

Create an array to hold the substring. First, Create a slice of a string for the first 8 characters and add it to the array Repeat slice logic for every 4 characters three times, pushes to array Finally, create a slice of string for the remaining 12 characters

Now, the Array contains a slice of substrings, Join these elements using a hyphen and return the string

![Ezoic](https://go.ezodn.com/utilcave_com/ezoicbwa.png "ezoic")

## Conclusion

Multiple approaches are specified here, To sum up, you can take whichever approach fits your application.

![Ezoic](https://go.ezodn.com/utilcave_com/ezoicbwa.png "ezoic")