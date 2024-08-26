
After creating a script
```
sudo chmod +x./ scriptname.sh
```

Adding this line with the shebang (!#) tells system what shell to use and tells you what type of script it is.
```
#!/bin/bash
```

To run a script in a local directory just type the path and file name
```sh
./scriptname.sh
```

Store and print variable
```
myName = "Lucky"
echo $myName
```

VARIABLES created in one session are lost when the session Ends.

![[Pasted image 20240621105306.png]]
To print a  string with variable contents it must be in double quotes.
Single quotes treat the variable name as part of the string

How to add the output of a command to a variable
```
files=$(ls)
```
This puts ls in a sub-shell, so you won't see the output of the ls, just see what it stored in the variable.

##### The etiquette is that variables should be lower case unless referencing a environment  variable.
##### `env` at the cl lists all environment variables.




