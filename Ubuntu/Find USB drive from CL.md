```
#List USB devices in Linux.
lsusb
lsusb -v

# See all PCI devices
lspci  

#Display USB device details
usb-devices
```
None of the found `uRaspbackup`  drive on Dell with Ubuntu 22.04
## Using the mount command to list the mounted USB devices

The mount command is used for mounting partitions in Linux. You can also list USB storage devices using the same command.

Generally, USB storage is mounted in the media directory. Thus, filtering the output of mount command on media will give you the desired result.

```
mount | grep media
```
This found `uRaspbackup`  on Dell with Ubuntu 22.04