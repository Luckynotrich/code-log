```sh
#!/bin/bash

declare -a indexs=$(ls -F dist/assets/index-*);
# OUTPUT: dist/assets/index-CkK8rj65.js dist/assets/index-kSRyaBIB.css

# prints number of characters
echo ${#indexs}

# removes files from directory
for word in $indexs
do
rm "$word";
done
```