Exit Codes help you determine whether a command is successful.
The `$?` contains a value representing the success/failure of the last command.

##### `echo $?` returns 0(zero) for success and something else for failure

```sh
#!/bin/bash

package=htop

sudo apt install $package

echo "The exit code for the package install is: $?"

```

##### Better utilizing exit code
```sh
#!/bin/bash

package=htop

sudo apt install $package

if [ $? -eq 0 ]
then
	echo "The installation of $package was successful."
	echo the new command is available here:"
	which $package
else
	echo "$package failed to install"
fi


```
##### Almost real world script
```sh
#!/bin/bash

package=htop

sudo apt install $package >> package_install_results.log

if [ $? -eq 0 ]
then
	echo "The installation of $package was successful."
	echo the new command is available here:" >> package_install_failure.log
	which $package
else
	echo "$package failed to install"
fi

```

##### `>>`  appends output to the end of a file
##### A Very Important Script
```sh
#!/bin/bash

directory=/etc

if [ -d $directory ]
then
	echo "The directory $directory exists."
else
	echo "The directory $directory doesn't exist."
fi

echo " the exit code for this script is $?"
```
This script outputs an exit code of 0 no matter whether the dir exists or not.

```sh
#!/bin/bash
echo "Hello world"
exit 1 
echo $?
```

`exit` causes script to never reach the `echo $?` and sets exit code to 1.

```sh
#!/bin/bash
directory=/etc
if [ -d $directory ]
then
	echo "The directory $directory exists."
	exit 0
else
	echo "The directory $directory doesn't exist."
	exit 199
fi
echo "Exit code = $?"
```