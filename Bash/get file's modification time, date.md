```sh
# Get the modification time in human-readable format
stat -c %y myfile.txt

# Get the modification time as seconds since the Epoch
stat -c %Y myfile.txt

# Get the modification time using date command
date -r myfile.txt

# Get the modification time in YYYY-MM-DD HH:MM:SS format
date -r myfile.txt "+%Y-%m-%d %H:%M:%S"
```

![[Pasted image 20250602092232.png]]

