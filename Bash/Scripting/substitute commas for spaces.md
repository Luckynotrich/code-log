```sh
#!/bin/bash
declare -a index1=$(ls -F dist/assets/index-*);

# substitute commas for spaces
declare -a index2=`echo $index1 | sed 's/ /,/g'`;

echo $index2
```