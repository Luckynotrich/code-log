
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

## To declare an array in bash

Let us declare an array called ‘array’ and assign three values called ‘one’, ‘two’, and ‘three’ when using bash:

```
array=( one two three )
```

Of course you can use the [declare command](https://bash.cyberciti.biz/guide/Declare_command "Declare command - Linux Bash Shell Scripting Tutorial Wiki") as follows too:

```
# Indexed arrays (numbered list starting from zero [0] )#
declare -a ARRAY_NAME_HERE=(value1 value2 .... valueN)
 
# Create array named 'nameserver' with three values
declare -a nameservers=(google cloudflare isp1)
 
# Add 4th element/value to array named 'nameserver'
nameservers[3]=isp2
```

Here are some more examples of bash array:

```
files=( "/etc/passwd" "/etc/group" "/etc/hosts" )
limits=( 10 20 26 39 48)
```

### A note about bash associative array (key/value pair)

The syntax is as follows to define associative arrays when using bash:

```
# associative arrays #
declare -A ARRAY_NAME_HERE
declare -A fruits
# Set key and values
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Where,

-   **declare -A fruits** – This line defines an associative array named fruits using the \-A option.
-   **fruits\[south\]="Banana"** – This line assigns the value “Banana” to the key “south” in the fruits array. In other words, it creates a mapping between say popular region names and fruits. You can then access the fruit associated with a direction using its key. For example, ${fruits\[south\]} would return “Banana”.

### Printing an array under bash

To print an array use the [printf command](https://bash.cyberciti.biz/guide/Printf_command "Printf command - Linux Bash Shell Scripting Tutorial Wiki") or [echo command](https://bash.cyberciti.biz/guide/Echo_Command "Echo Command - Linux Bash Shell Scripting Tutorial Wiki") as follows:

```
printf "%s\n" "${array[@]}"
printf "%s\n" "${files[@]}"
printf "%s\n" "${limits[@]}"
printf "%s\n" "${fruits[@]}"
```

This will print everything stored in the array:

```
Passion Fruit
Orange
Pineapple
Banana

```

You can access elements using index number such as 0, 1, 2. You can use key values such as ‘south’, ‘north’ under bash. For example:

```
printf "Group file in Linux or Unix: %s\n" "${files[1]}"
printf "Popular fruit in South India: %s\n" "${fruits[south]}"
```

[![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash.png)

Click to enlarge

### How to iterate over keys or values

Let us see example that demonstrate the basic usage of key-value arrays in Bash. First, define the array and add the values::

```
# The `-A` option specifies that the fruits array is an associative array
# --
declare -A fruits
# --
# Associative arrays are a type of array in Bash where the elements are 
# associated with keys as follows.
# --
# Initialize the fruits array with four elements. 
# The elements are associated with the keys south, north, west, and east. 
# The values associated with the elements are Banana, Orange, Passion Fruit, and Pineapple.
# --
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Now, here is how to iterate over keys:

```
for key in "${!fruits[@]}"
do
  echo "Key for fruits array is: $key"
done
```

And, here is how to iterate over values:

```
for value in "${fruits[@]}"
do
  echo "Value for fruits array is: $value"
done
```

Finally, you can print key and value pair, which is what you need in most cases:

```
for key in "${!fruits[@]}"
do
  echo "Key is '$key'  => Value is '${fruits[$key]}'"
done
```

The above bash or loop iterates through the fruits array. The for loop uses the special variable **!fruits\[@\]**, which contains a list of all the keys in the fruits array. In each iteration of the loop, the current key is assigned to the variable key. The value associated with the key is then printed to the Linux or Unix screen as follows using **${fruits\[$key\]}**:

```
Key is 'west'  => Value is 'Passion Fruit'
Key is 'north'  => Value is 'Orange'
Key is 'east'  => Value is 'Pineapple'
Key is 'south'  => Value is 'Banana'

```

## Bash for loop array example to iterate through array values

Use [bash for loop](https://www.cyberciti.biz/faq/bash-for-loop/) syntax as follows:

```
for i in "${arrayName[@]}"
do
   : 
   # do whatever on "$i" here
done
```

The $i variable will hold each item in an array. Do not skip double quotes around the ${arrayName\[@\]}.

## Loop through an array of strings in Bash

Here is a sample working script:

```
#!/bin/bash
# declare an array called array and define 3 vales
array=( one two three )
for i in "${array[@]}"
do
echo "$i"
done
```

Run it as follows using the chmod command:  

## To declare an array in bash

Let us declare an array called ‘array’ and assign three values called ‘one’, ‘two’, and ‘three’ when using bash:

```
array=( one two three )
```

Of course you can use the [declare command](https://bash.cyberciti.biz/guide/Declare_command "Declare command - Linux Bash Shell Scripting Tutorial Wiki") as follows too:

```
# Indexed arrays (numbered list starting from zero [0] )#
declare -a ARRAY_NAME_HERE=(value1 value2 .... valueN)
 
# Create array named 'nameserver' with three values
declare -a nameservers=(google cloudflare isp1)
 
# Add 4th element/value to array named 'nameserver'
nameservers[3]=isp2
```

Here are some more examples of bash array:

```
files=( "/etc/passwd" "/etc/group" "/etc/hosts" )
limits=( 10 20 26 39 48)
```

### A note about bash associative array (key/value pair)

The syntax is as follows to define associative arrays when using bash:

```
# associative arrays #
declare -A ARRAY_NAME_HERE
declare -A fruits
# Set key and values
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Where,

-   **declare -A fruits** – This line defines an associative array named fruits using the \-A option.
-   **fruits\[south\]="Banana"** – This line assigns the value “Banana” to the key “south” in the fruits array. In other words, it creates a mapping between say popular region names and fruits. You can then access the fruit associated with a direction using its key. For example, ${fruits\[south\]} would return “Banana”.

### Printing an array under bash

To print an array use the [printf command](https://bash.cyberciti.biz/guide/Printf_command "Printf command - Linux Bash Shell Scripting Tutorial Wiki") or [echo command](https://bash.cyberciti.biz/guide/Echo_Command "Echo Command - Linux Bash Shell Scripting Tutorial Wiki") as follows:

```
printf "%s\n" "${array[@]}"
printf "%s\n" "${files[@]}"
printf "%s\n" "${limits[@]}"
printf "%s\n" "${fruits[@]}"
```

This will print everything stored in the array:

```
Passion Fruit
Orange
Pineapple
Banana

```

You can access elements using index number such as 0, 1, 2. You can use key values such as ‘south’, ‘north’ under bash. For example:

```
printf "Group file in Linux or Unix: %s\n" "${files[1]}"
printf "Popular fruit in South India: %s\n" "${fruits[south]}"
```

[![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash.png)

Click to enlarge

### How to iterate over keys or values

Let us see example that demonstrate the basic usage of key-value arrays in Bash. First, define the array and add the values::

```
# The `-A` option specifies that the fruits array is an associative array
# --
declare -A fruits
# --
# Associative arrays are a type of array in Bash where the elements are 
# associated with keys as follows.
# --
# Initialize the fruits array with four elements. 
# The elements are associated with the keys south, north, west, and east. 
# The values associated with the elements are Banana, Orange, Passion Fruit, and Pineapple.
# --
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Now, here is how to iterate over keys:

```
for key in "${!fruits[@]}"
do
  echo "Key for fruits array is: $key"
done
```

And, here is how to iterate over values:

```
for value in "${fruits[@]}"
do
  echo "Value for fruits array is: $value"
done
```

Finally, you can print key and value pair, which is what you need in most cases:

```
for key in "${!fruits[@]}"
do
  echo "Key is '$key'  => Value is '${fruits[$key]}'"
done
```

The above bash or loop iterates through the fruits array. The for loop uses the special variable **!fruits\[@\]**, which contains a list of all the keys in the fruits array. In each iteration of the loop, the current key is assigned to the variable key. The value associated with the key is then printed to the Linux or Unix screen as follows using **${fruits\[$key\]}**:

```
Key is 'west'  => Value is 'Passion Fruit'
Key is 'north'  => Value is 'Orange'
Key is 'east'  => Value is 'Pineapple'
Key is 'south'  => Value is 'Banana'

```

## Bash for loop array example to iterate through array values

Use [bash for loop](https://www.cyberciti.biz/faq/bash-for-loop/) syntax as follows:

```
for i in "${arrayName[@]}"
do
   : 
   # do whatever on "$i" here
done
```

The $i variable will hold each item in an array. Do not skip double quotes around the ${arrayName\[@\]}.

## Loop through an array of strings in Bash

Here is a sample working script:

```
#!/bin/bash
# declare an array called array and define 3 vales
array=( one two three )
for i in "${array[@]}"
do
echo "$i"
done
```

Run it as follows using the chmod command:  

## To declare an array in bash

Let us declare an array called ‘array’ and assign three values called ‘one’, ‘two’, and ‘three’ when using bash:

```
array=( one two three )
```

Of course you can use the [declare command](https://bash.cyberciti.biz/guide/Declare_command "Declare command - Linux Bash Shell Scripting Tutorial Wiki") as follows too:

```
# Indexed arrays (numbered list starting from zero [0] )#
declare -a ARRAY_NAME_HERE=(value1 value2 .... valueN)
 
# Create array named 'nameserver' with three values
declare -a nameservers=(google cloudflare isp1)
 
# Add 4th element/value to array named 'nameserver'
nameservers[3]=isp2
```

Here are some more examples of bash array:

```
files=( "/etc/passwd" "/etc/group" "/etc/hosts" )
limits=( 10 20 26 39 48)
```

### A note about bash associative array (key/value pair)

The syntax is as follows to define associative arrays when using bash:

```
# associative arrays #
declare -A ARRAY_NAME_HERE
declare -A fruits
# Set key and values
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Where,

-   **declare -A fruits** – This line defines an associative array named fruits using the \-A option.
-   **fruits\[south\]="Banana"** – This line assigns the value “Banana” to the key “south” in the fruits array. In other words, it creates a mapping between say popular region names and fruits. You can then access the fruit associated with a direction using its key. For example, ${fruits\[south\]} would return “Banana”.

### Printing an array under bash

To print an array use the [printf command](https://bash.cyberciti.biz/guide/Printf_command "Printf command - Linux Bash Shell Scripting Tutorial Wiki") or [echo command](https://bash.cyberciti.biz/guide/Echo_Command "Echo Command - Linux Bash Shell Scripting Tutorial Wiki") as follows:

```
printf "%s\n" "${array[@]}"
printf "%s\n" "${files[@]}"
printf "%s\n" "${limits[@]}"
printf "%s\n" "${fruits[@]}"
```

This will print everything stored in the array:

```
Passion Fruit
Orange
Pineapple
Banana

```

You can access elements using index number such as 0, 1, 2. You can use key values such as ‘south’, ‘north’ under bash. For example:

```
printf "Group file in Linux or Unix: %s\n" "${files[1]}"
printf "Popular fruit in South India: %s\n" "${fruits[south]}"
```

[![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

![Linux Loop through an array of strings in Bash](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash-599x404.png)

](https://www.cyberciti.biz/media/new/faq/2008/04/Linux-Loop-through-an-array-of-strings-in-Bash.png)

Click to enlarge

### How to iterate over keys or values

Let us see example that demonstrate the basic usage of key-value arrays in Bash. First, define the array and add the values::

```
# The `-A` option specifies that the fruits array is an associative array
# --
declare -A fruits
# --
# Associative arrays are a type of array in Bash where the elements are 
# associated with keys as follows.
# --
# Initialize the fruits array with four elements. 
# The elements are associated with the keys south, north, west, and east. 
# The values associated with the elements are Banana, Orange, Passion Fruit, and Pineapple.
# --
fruits[south]="Banana"
fruits[north]="Orange"
fruits[west]="Passion Fruit"
fruits[east]="Pineapple"
```

Now, here is how to iterate over keys:

```
for key in "${!fruits[@]}"
do
  echo "Key for fruits array is: $key"
done
```

And, here is how to iterate over values:

```
for value in "${fruits[@]}"
do
  echo "Value for fruits array is: $value"
done
```

Finally, you can print key and value pair, which is what you need in most cases:

```
for key in "${!fruits[@]}"
do
  echo "Key is '$key'  => Value is '${fruits[$key]}'"
done
```

The above bash or loop iterates through the fruits array. The for loop uses the special variable **!fruits\[@\]**, which contains a list of all the keys in the fruits array. In each iteration of the loop, the current key is assigned to the variable key. The value associated with the key is then printed to the Linux or Unix screen as follows using **${fruits\[$key\]}**:

```
Key is 'west'  => Value is 'Passion Fruit'
Key is 'north'  => Value is 'Orange'
Key is 'east'  => Value is 'Pineapple'
Key is 'south'  => Value is 'Banana'

```

## Bash for loop array example to iterate through array values

Use [bash for loop](https://www.cyberciti.biz/faq/bash-for-loop/) syntax as follows:

```
for i in "${arrayName[@]}"
do
   : 
   # do whatever on "$i" here
done
```

The $i variable will hold each item in an array. Do not skip double quotes around the ${arrayName\[@\]}.

## Loop through an array of strings in Bash

Here is a sample working script:

```
#!/bin/bash
# declare an array called array and define 3 vales
array=( one two three )
for i in "${array[@]}"
do
echo "$i"
done
```

Run it as follows using the chmod command: