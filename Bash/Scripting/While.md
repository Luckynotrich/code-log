```sh
#!/bin/bash

myvar=1
while [  $myvar -le 10 ]
do
	echo $myvar
	myvar=$(($myvar +1))
	sleep 0.5
done
```

##### `-le` less than or equal
 
 loops until some one or some thing rm's it.
```sh
#!/bin/bash
clear
touch ~/testfile
length=7
start=$(date +%s)
echo "file is created at $start"
sleep 3
while [ -f ~/testfile ]
do
	end=$(date +%s)
	ttime=$(($end-$start))
	if [ $ttime -gt $length ]
	then
		rm ~/testfile
	else
		clear;
		echo "The file still exists after $ttime"
	fi
done

echo "The file is gone as of $ttime and so am I!"
```
https://www.youtube.com/watch?v=R0tTsdQ_9Vw&list=PLT98CRl2KxKGj-VKtApD8-zCqSaN2mD4w&index=7
