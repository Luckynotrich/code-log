Standard Output, Standard Error and Standard Input

**Standard Output** is output printed to the screen as a result of commands that doesn't qualify as **Standard Error**.

**Standard Error** ex:
![[Pasted image 20240624122604.png]]
Checking the exit code (`echo $?`) will reveal a non-zero value.

**Standard Output** can have **Standard Error** mixed in it.

E.g.: Permission denied on some files mixed in with successfully found files in a find command.
Compare
```
find /etc -type f
```
output to
```
find /etc -type f 2> /dev/null
```
which moves all output which results in  a 2 or greater exit code to `/dev/null` which is the same as deleting it.
 Conversely, 
 ```
 find /etc -type f 1> /dev/null
```
will only print **Standard Error** to the screen. The `1` is optional in this statement
Equivalent to:
```
find /etc -type f > /dev/null
```

##### Collecting SO and SE
```sh
find /etc -type f >find_results.txt 2>find_errors.txt
```

Here is a functional example. 
```sh
#!/bin/bash
#!/bin/bash
#
# implemented in /usr/local/bin/update
#
#
release_file=/etc/os-release
logfile=/var/log/updater.log
errorlog=/var/log/updater_errors.log

if grep -q "Arch" $release_file
then
        # The host is based on Arch, run the pacman update command
        sudo pacman -Syu 1>>$logfile 2>>$errorlog
        if [ $? -ne 0 ]
        then
                echo "An error occurred, please check the $errorlog."
                fi
fi

if grep -q "Debian" $release_file || grep -q "Ubuntu" $release_file
then
        # The host is based on Devian or Ubuntu,
        # Rin the apt version of the command
        sudo apt update 1>>$logfile 2>>$errorlog
        if [ $? -ne 0 ]
        then
                echo "An error occurred, please check the $errorlog."
                fi
                      # -y causes script to complete w/o prompting user
        sudo apt dist-upgrade -y 1>>$logfile 2>>$errorlog 
        if [ $? -ne 0 ]
        then
                echo "An error occurred, please check the $errorlog."
                fi
fi

```

## Standard Input

```sh
#!/bin/bash

echo "Please enter your name:"
read myname
echo "Your name is: $myname"
```