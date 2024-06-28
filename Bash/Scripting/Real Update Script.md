##### Universal Update Script
Version 1 - would fail if someone created the directory being tested for
```sh
#!/bin/bash

if [ -d /etc/pacman.d ]
then
	# The host is based on Arch, run the pacman update command
	sudo pacman -Syu
fi

if [ -d /etc/apt ]
then 
	# The host is based on Devian or Ubuntu,
	# Rin the apt version of the command
	sudo apt update
	sudo apt dist-upgrade
fi
```

Version 2 - only works on Arch or Ubuntu
```sh
#!/bin/bash
release_file=/etc/os-release
if grep -q "Arch" $release_file
then
	# The host is based on Arch, run the pacman update command
	sudo pacman -Syu
fi

if grep -q "Ubuntu" $release_file
then 
	# The host is based on Ubuntu,
	# Rin the apt version of the command
	sudo apt update
	sudo apt dist-upgrade
fi
```

Version 3 - uses `||` to combine Debian and Ubuntu
```sh
#!/bin/bash
release_file=/etc/os-release
if grep -q "Arch" $release_file
then
	# The host is based on Arch, run the pacman update command
	sudo pacman -Syu
fi

if grep -q "Debian" $release_file || grep -q "Ubuntu" $release_file
then 
	# The host is based on Devian or Ubuntu,
	# Rin the apt version of the command
	sudo apt update
	sudo apt dist-upgrade
fi
```

Version 4 - using **Standard Output** and **Standard Error** and  **Redundancy** :(
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
        sudo apt dist-upgrade -y 1>>$logfile 2>>$errorlog
        if [ $? -ne 0 ]
        then
                echo "An error occurred, please check the $errorlog."
                fi
fi

```

Final version - **No Redundancy**
```sh
#!/bin/bash
#!/bin/bash
#
# implemented in /usr/local/bin/update
#
#
output_if_errors(){
 if [ $? -ne 0 ]
        then
                echo "An error occurred, please check the $errorlog."
                fi
fi
}
release_file=/etc/os-release
logfile=/var/log/updater.log
errorlog=/var/log/updater_errors.log

if grep -q "Arch" $release_file
then
        # The host is based on Arch, run the pacman update command
        sudo pacman -Syu 1>>$logfile 2>>$errorlog
	    output_if_errors

if grep -q "Debian" $release_file || grep -q "Ubuntu" $release_file
then
        # The host is based on Devian or Ubuntu,
        # Run the apt version of the command
        sudo apt update 1>>$logfile 2>>$errorlog
        output_if_errors
        sudo apt dist-upgrade -y 1>>$logfile 2>>$errorlog
        output_if_errors
fi


