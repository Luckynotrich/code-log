### Step 1: Update/Upgrade Package Repository
```sh
sudo apt update 
```


```sh
sudo apt upgrade
```

or
```sh
sudo apt full-upgrade
```


### Step 2: Install MySQL
```sh
sudo apt install mysql-server
```

Check version
```sh
mysqld --version
```

### Step 3: Securing MySQL

After installing MySQL, the next step is to perform an initial security setup for your MySQL installation. Securing includes setting a [strong password](https://phoenixnap.com/blog/strong-great-password-ideas), removing unnecessary accounts and [databases](https://phoenixnap.com/kb/what-is-a-database), and restricting access to enhance overall security.

First make sure its running:
```sh
sudo systemctl status mysql.service
```
If you see
![[Pasted image 20240823083508.png]]
Try:
```sh
sudo systemctl unmask mysql.service
```
Then:
```sh
sudo service mysql start
```
if you see:
![[Pasted image 20240823102744.png]]

try:
```sh
sudo find / -type s | grep mysqld.sock
```
If this is unsuccessful
try:
```sh
sudo ls -la /var/run/
```
try:
```sh
sudo mkdir /var/run/mysqld
sudo chown mysql:mysql /var/run/mysqld/
sudo chmod -R 755 /var/run/mysqld/
```

To secure the installation, run the following command:

```
sudo mysql_secure_installation
```

If you see:
![[Pasted image 20240823113353.png]]
