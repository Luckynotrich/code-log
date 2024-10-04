### [Cheatography](https://cheatography.com/davechild/cheat-sheets/regular-expressions/)

\b      -   character strings boundary - any character that might end a word 
[a-z]   -   alpha numeric lower case complete set

quantifiers:
`*`       -   zero or more
`+`      -   one or more
`?`       -   zero or one

example:
`\b[a-e]+\b`   - finds all words containing only a though e

`^`       -   negation
`\s`      -   space character

example:
`\b[^aeiou\s]+\b`  - select only strings w/o first 5 lower case vowels and white space

`{}` meta character for specification such a quantity
example:
`\b[a-z]{3}\b`        - select only lower case alpha strings of length 3
`\b[a-z]{3,4}\b`    - select only lower case alpha strings of length 3 or 4
`\b[a-z]{5,}\b`    - select only lower case alpha strings of length 5 or more

![[Pasted image 20240924100911.png]]

`\w`            -               -  Word
ex:    `\b\w{3}\b`      -  find alpha strings of length 3

`\W`           -         Not a word

`|`            -         OR
ex::   `(b|c)at`          - matches bat or cat

`.`           -                - dot matches everything
`\`          -                 - escape special character
ex:  `[A-Z].*\.`      - find string that begins with upper alpha and ends with a dot

##### Anchors
`^`       -              - Start of a string 
`$`      -              - End of a string
ex:  `^[A-Z]. *\.$`       - find strings that begin with a upper alpha and end with a dot

