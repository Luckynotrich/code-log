```sh
#!/bash/bin
echo "You entered the argument: $1, $2 ,$3 and $4"
```

Counting objects in `$1` directory
```sh
#!/bin/bash

# pipes ls results to word count (wc) and stores its output in lines
lines=$(ls -lh $1 | wc -l)

# outputs lines-1 because wc counts the 'total' output by ls as a word
echo "You have $(($lines-1)) objects in the $1 directory."
```