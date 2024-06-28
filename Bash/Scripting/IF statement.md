##### `if then else elif fi`  a space between `if` and `[` and `conditional` and `]` is required.

```sh
#!/bin/bash

mynum=200

if [ $mynum -eq 200 ]
then
  echo "The condition is true."
else 
	echo "The var does not equal 200."
fi
```

###### `-eq` checks equality
###### `! var -eq value` checks inequality

###### `var -ne value`  not equal
###### `-gt` greater than
###### `-lt` less than
##### `-le` less than or equal
##### `-ge` greater than or equal

```sh
#!/bin/bash
if [ -f ./myfile ]
then
	echo "The file exists."
else
	touch myfile
	echo "The file is being created"
fi

```

###### `-f` does file exist
##### `-d` does directory exist

installs and/or runs `htop`
```sh
#!/bin/bash

command=htop

if command -v $command
then
	echo "$command is availabel, lets run it..."
else
	echo "$command is NOT available, installing it..."
	sudo apt update && sudo apt install -y $command
fi

$command
```
The `-y` tell the script to just run the install

The `[ ]` invokes the test command
###### `command -v` checks for the existence of a command like `htop`.  It is a standard linux command.

##### Logical operators

`||` OR
`&&` AND
