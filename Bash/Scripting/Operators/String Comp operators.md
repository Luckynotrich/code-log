### String comparison operators

String comparison operators enable the comparison of alphanumeric strings of characters. There are only a few of these operators, which are listed in Figure 3.

|Operator|Description|
|---|---|
|-z string|True if the length of string is zero|
|-n string|True if the length of string is non-zero|
|string1 == string2  <br>  <br>or  <br>  <br>string1 = string2|True if the strings are equal; a single **=** should be used with the test command for POSIX conformance. When used with the **[[** command, this performs pattern matching as described above (compound commands).|
|string1 != string2|True if the strings are not equal|
|string1 < string2|True if string1 sorts before string2 lexicographically (refers to locale-specific sorting sequences for all alphanumeric and special characters)|
|string1 > string2|True if string1 sorts after string2 lexicographically|