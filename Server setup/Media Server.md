installed Ubuntu 23.04 August 28 2023
Included Docker Snap and Postgresql Snap in install

To add a server to known_hosts: [Jack Wallen](https://www.techrepublic.com/article/how-to-easily-add-an-ssh-fingerprint-to-your-knownhosts-file-in-linux/)
```
ssh-keyscan -H 192.168.50.83 >> ~/.ssh/known_hosts
```
To view/edit known_hosts: 
```
vi /home/lucky/.ssh/known_hosts
```
Login before added name to known_host 
```
ssh richard@192.168.50.83 
```
apt list --upgradable

#### added host's name to /etc/hosts file
```
192.168.50.83   mediaserver
```
#### Alarm on first login attempt:
Suggests someone might be doing a "Man-in-the-Middle" attack and tells you to run a command similar to this:

```
ssh-keygen -f "/home/lucky/.ssh/known_hosts" -R "mediaserver"
```
This modifies the known_hosts file with the server public key

#### Now you can login with host's name
```
richard@mediaserver

```
#### Created static path on router.asus.com

[How to find the number of manually assigned IPs in the DHCP server?](https://www.asus.com/support/FAQ/1000906/)
Used the link above to set named path to: mediaserver 

[How to check the IP address and set up a Static/specific IP address using ASUSWRT?](https://www.asus.com/support/FAQ/114068/)
The link above is a little helpful, but relies on Windows

[How to set up Static Routes in ASUS Router?](https://www.asus.com/us/support/FAQ/1011706/)
 Doesn't make clear where much of the critical info can be found in the router interface.


![[Pasted image 20230829074940.png]]
![[Pasted image 20230828150033.png]]
![[Pasted image 20230829093319.png]]
![[Pasted image 20230829093628.png]]