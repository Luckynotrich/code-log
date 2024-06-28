
Version 1 - uses array literal which is not convenient 
```sh
#!/bin/bash

for current_number in 1 2 3 4 5 6 7 8 9 10
do
	echo $current_number
	sleep 1
done

echo "This is outside of the for loop."
```

Version 2 - uses array definition
```sh
#!/bin/bash
clear
for current_number in {1..10}
do
	echo $current_number
	sleep 1
done

echo "This is outside of the for loop."
```

More Useful For loop 
```sh
#!/bin/bash
# Check if logfiles dir exists
if [ -d logfiles ] 
then
	# if logfiles exists, delete it. 
	rm -rf logfile/
fi
# make a new logfiles directory
mkdir logfiles

# copy .log files to logfiles/
cp /var/log/*.log logfiles/
sleep 2
for file in logfiles/*.log
do
	# tar each file into a zip file
	tar -czvf $file.tar.gz $file
done
```