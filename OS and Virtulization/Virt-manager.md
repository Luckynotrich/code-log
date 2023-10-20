Managing Virtual Machines Remotely
To determine if CPU supports virtualization
```
egrep -c '(vmx|svm)' /proc/cpuinfo
```
A return larger than 0 is positive

Run: 'kvm-ok' find whether virtualization is enabled

Now see if your running kernel is 64-bit, just issue the following command:

```
uname -m
```

**x86_64** indicates a running 64-bit kernel. If you use see i386, i486, i586 or i686, you're running a 32-bit kernel.

Note: x86_64 is synonymous with amd64.

How to install qemu-kvm, virt-manager and libvirt Ubuntu 23.04 server
1) sudo apt update
2) 
```
sudo apt install qemu-kvm virt-manager virtinst libvirt-clients bridge-utils libvirt-daemon-system -y
```
![[Pasted image 20230828113648.png]]

![[Pasted image 20230828110658.png]]

How to find out if libvertd is running on Ubuntu 23.04
```
sudo systemctl status libvertd
```
