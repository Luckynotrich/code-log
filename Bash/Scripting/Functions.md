```sh
check_exit_status(){
	if [ $? -ne 0 ]
	then
		echo "An error occurred, please check the $errorlog file."
}
check_exit_status
```
