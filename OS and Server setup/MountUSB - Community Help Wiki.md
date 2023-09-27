Contents

1.  [Introduction](https://help.ubuntu.com/community/Mount/USB#Introduction)
2.  [Automounting](https://help.ubuntu.com/community/Mount/USB#Automounting)
    1.  [Mounting](https://help.ubuntu.com/community/Mount/USB#Mounting)
    2.  [Configuring Automounting](https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting)
    3.  [Configuring Program Autostart](https://help.ubuntu.com/community/Mount/USB#Configuring_Program_Autostart)
    4.  [Auto-mounting (Ubuntu Server)](https://help.ubuntu.com/community/Mount/USB#Auto-mounting_.28Ubuntu_Server.29)
3.  [Manually Mounting](https://help.ubuntu.com/community/Mount/USB#Manually_Mounting)
    1.  [Using Disks](https://help.ubuntu.com/community/Mount/USB#Using_Disks)
    2.  [Using mount](https://help.ubuntu.com/community/Mount/USB#Using_mount)
    3.  [Using pmount](https://help.ubuntu.com/community/Mount/USB#Using_pmount)
4.  [The Importance of Unmounting](https://help.ubuntu.com/community/Mount/USB#The_Importance_of_Unmounting)
5.  [Other Useful Commands](https://help.ubuntu.com/community/Mount/USB#Other_Useful_Commands)
6.  [Troubleshooting](https://help.ubuntu.com/community/Mount/USB#Troubleshooting)
    1.  [Interfering services](https://help.ubuntu.com/community/Mount/USB#Interfering_services)
    2.  [Unclean LogFile](https://help.ubuntu.com/community/Mount/USB#Unclean_LogFile)
    3.  [User Privileges](https://help.ubuntu.com/community/Mount/USB#User_Privileges)
    4.  [Preferences](https://help.ubuntu.com/community/Mount/USB#Preferences)
    5.  [USB 2 Issues](https://help.ubuntu.com/community/Mount/USB#USB_2_Issues)
    6.  [Buffer I/O Errors](https://help.ubuntu.com/community/Mount/USB#Buffer_I.2FO_Errors)
    7.  [Device suddenly becomes read-only](https://help.ubuntu.com/community/Mount/USB#Device_suddenly_becomes_read-only)
    8.  [USB-Device is or becomes read-only without errors](https://help.ubuntu.com/community/Mount/USB#USB-Device_is_or_becomes_read-only_without_errors)
    9.  [General tip](https://help.ubuntu.com/community/Mount/USB#General_tip)
    10.  [Seeking Further Help](https://help.ubuntu.com/community/Mount/USB#Seeking_Further_Help)
7.  [Other Resources](https://help.ubuntu.com/community/Mount/USB#Other_Resources)

## Introduction

This page explains how to use USB drives, like external hard disks and USB flash drives (aka USB sticks, thumb drives, pen drives, etc). The material here also applies to flash cards (like in your digital camera).

USB storage devices have the enormous advantage that for the most part they use a standard set of protocols. Thus, instead of needing individual drivers, as does much computer hardware, a standard driver permits access to the devices, making them very portable and able to easily work on many platforms.

![IconsPage/stop.png](https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=stop.png "IconsPage/stop.png")

For help with internal hard drives, see [Fstab](https://help.ubuntu.com/community/Fstab) and [MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions).

## Automounting

## Mounting

By default, storage devices that are plugged into the system mount automatically in the **/media/<username>** directory, open a file browser window for each volume and place an icon on your desktop. The rationale for this slight change of behavior can be found [here](http://ubuntuforums.org/showthread.php?t=2152773&p=12683721#post12683721). If you plug in a usb hard disk with many partitions, all of the partitions will automatically mount. This behaviour may not be what you want; you can configure it as shown below.

If the volumes have labels the icons will be named accordingly. Otherwise, they will be named **"disk"**, **"disk-1"** and so on.

To change the volume label see [RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).

## Configuring Automounting

To enable or disable automount open a terminal and type:

```
dconf-editor
```

Browse to **org.gnome.desktop.media-handling**.

The **automount** key controls whether to automatically mount media. If set to true, Nautilus will automatically mount media such as user-visible hard disks and removable media on start-up and media insertion.

Another key, **org.gnome.desktop.media-handling.automount-open**, controls whether to automatically open a folder for automounted media.

If set to true, Nautilus will automatically open a folder when media is automounted. This only applies to media where no known x-content type was detected; for media where a known x-content type is detected, the user configurable action will be taken instead. This can be configured as shown below.

## Configuring Program Autostart

To control which programs automatically start when you plug in a device, go to **System-Settings - Details - Removable Media**.

For more complex scenarios, see [UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto).

### Unmounting/Ejecting

Before you disconnect the device, don't forget to unmount it. This can be done in one of the following ways:

-   Right-click the desktop icon and select "Unmount" (or in some cases, "Eject").
-   In the file manager window, click on the "eject" button next to the name of the mounted volume.
-   Right-click the icon in the launcher and select "Unmount".

## Auto-mounting (Ubuntu Server)

By default, disk drives do not auto-mount in Ubuntu Server Edition. If you are looking for a lightweight solution that does not depend on HAL/DBUS, you can install "usbmount".

###  Manually Mounting

## Using Disks

**Disks** (the GNOME disk utility) is an application for visually managing disk drives and media. When you run it, you will see a list of your drives, including USB drives. If you click a drive on the list, you can view its details, and you can click the triangle-shaped button (Play button) to mount the drive. (This method works even when the drive does not auto-mount.) 

### Installing Disks
```
sudo apt update
```
```
sudo apt install gnome-disk-utility
```

## Using mount

### Get the Information

Sometimes, devices don't automount, in which case you should try to manually mount them. First, you must know what device you are dealing with and what filesystem it is formatted with. Most flash drives are FAT16 or FAT32 and most external hard disks are NTFS. Type the following:

```
sudo fdisk -l
```

Find your device in the list. It is probably something like /dev/sdb1. For more information about filesystems, see [LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained).

### Create the Mount Point

Now we need to create a mount point for the device. Let's say we want to call it "external". You can call it whatever you want, but if you use spaces in the name it gets a little more complicated. Instead, use an underscore to separate words (like "my\_external"). Create the mount point:

```
sudo mkdir /media/external
```
#### Using df  -T
When you want to identify the filesystem type on Linux, the first command that comes to mind may be `df`, which is a standard Linux command that reports disk space usage. However, `df` command (with `-T` option) is only useful to show the filesystem type for _mounted_ devices. The`df` command does not show any information about a USB device which is plugged in, but _not_ mounted

#### Using lsblk
The first command you can use is `lsblk`, which shows information about available block devices. This command can read information of a block device whether or not it is mounted. When run wlith `-f` option, it shows filesystem type of every mounted or unmounted block device.
![[Pasted image 20230924123352.png]]
### Mount the Drive

We can now mount the drive. Let's say the device is /dev/sdb1, the filesystem is FAT16 or FAT32 (like it is for most USB flash drives), and we want to mount it at /media/external (having already created the mount point):

```
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```

The options following the "-o" give you ownership of the drive, and the masks allow for extra security for file system permissions. If you don't use those extra options you _may_ not be able to read and write the drive with your regular username.

Otherwise, if the device is formatted with NTFS, run:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/external
```

  
Note: You must have the ntfs-3g driver installed. See [MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) for more information.  
  

### Unmounting the Drive

When you are finished with the device, don't forget to unmount the drive before disconnecting it. Assuming /dev/sdb1 is mounted at /media/external, you can either unmount using the device or the mount point:

```
sudo umount /dev/sdb1
```

or:

```
sudo umount /media/external
```

You cannot unmount from the desktop by right-clicking the icon if the drive was manually mounted.

## Using pmount

There is a program called pmount available in the [repositories](https://help.ubuntu.com/community/Repositories/Ubuntu) which allows unprivileged users to mount drives as if they were using sudo, even without an entry in [/etc/fstab](https://help.ubuntu.com/community/Fstab). This is perfect for computers that have users without [RootSudo](https://help.ubuntu.com/community/RootSudo) access, like public terminals or thin clients.

pmount can be used with the same syntax as mount (but without sudo), or quite simply as follows:

```
pmount <device> [ label ] 
```

Example:

-   ```
     pmount /dev/sdb1 flash_drive
    ```
    
    This will mount the device /dev/sdb1 at /media/flash\_drive.

If you leave off the _label_ option, it will mount by default at /media/device.

To unmount the device, use pumount, like so:

```
pumount <device>
```

Example:

-   ```
     pumount /dev/sdb1
    ```
    

For more help, see the man pages for [pmount](http://linux.die.net/man/1/pmount) and [pumount](http://linux.die.net/man/1/pumount).

## The Importance of Unmounting

![IconsPage/tip.png](https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=tip.png "IconsPage/tip.png")

Before disconnecting devices, you must unmount them first. This is similar to "Safely Remove" in Windows in that the device won't unmount until data is finished being written to the device, or until other programs are finished using it. This applies to all types of storage devices, including flash drives, flash cards, external hard drives, ipods and other media players, and even remote storage like Samba or NFS shares.

**Failure to unmount before disconnecting the device can result in loss of data and/or a corrupted file system.** There are no exceptions to this rule. Be safe - unmount your drives before disconnecting them!

## Other Useful Commands

To see a list of your USB devices (the vendor and device ID's), run:

```
lsusb
```

To see all attached storage devices and their partitions, run:

```
sudo fdisk -l
```

To see information about currently mounted systems, simply run:

```
mount
```

## Troubleshooting

Presented here are some common problems users encounter.

## Interfering services

Two services/programs responsible for automounting might interfere and thereby prevent a successful automount and permission setting.

Example: Activating the Automount function of Nautilus while using pmount will result in read-only permissions for normal users. Either disable Nautilus' Automount function or deinstall pmount.

## Unclean LogFile

If you are mounting drives formatted with NTFS (like most external USB hard disks are), you must first have the ntfs-3g driver installed. This is done automatically in newer versions of Ubuntu. You should also install ntfs-config and enable mounting, which is not done automatically. For ntfs-3g and ntfs-config, see [MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions).

When a drive is not Safely Removed from a Windows machine (or a forced shutdown occurs from Windows), you may get an error like this when you plug in your drive:

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force
```

The best option is Choice 1, but you can force the mount by running Choice 2 with sudo. You must then manually unmount it from the terminal (you can't right click the desktop icon):

```
sudo umount <mount_point>
```

After that the drive should automount normally again.

## User Privileges

If your usb device doesn't appear on your desktop, you should check that your user has the correct privileges. Go to **System->Administration->User and Groups**, choose the user, click on "Properties", then go to the "User Privileges" tab. You should have the "Access external storage devices automatically" option checked.

## Preferences

If your usb device doesn't appear on your desktop, you should check that the automount action is enabled in the preferences:

-   Navigate to **System->Preferences->Removable Drives and Media**
    
-   Verify that all "Mount removable drives when..." are checked.

NOTE: This does not seem to apply to Hardy Heron.

## USB 2 Issues

### old kernels workaround

If you encounter problems using your USB device with USB 2 (i.e. 'high speed' mode), you can revert to the 'full speed' mode (slower) by unloading ehci\_hcd. To do that, type in a terminal:

```
sudo rmmod ehci_hcd
```

before plugging in your device.

### recent kernels workaround, from Karmic

see also [AbsolutelyTech](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd)

ehci\_hcd is now built into the kernel and cannot be load/unloaded using modprobe. To revert a connected device from (failing) high-speed to full-speed:

-   Determine your device id using
    
    ```
     lsusb
    ```
    
-   Find which bus it is connected to. The bus id can be found as a folder in /sys/bus/pci/drivers/ehci\_hcd. The following script explores buses and connected devices:
    
    ```
    pushd /sys/bus/pci/drivers/ehci_hcd > /dev/null
    for bus in 0000:??:??.? ; do
            echo "ehci_hcd bus $bus"
            pushd $bus/usb1 > /dev/null
            for dev in ?-?; do
                    idVendor=`cat $dev/idVendor`
                    idProduct=`cat $dev/idProduct`
                    echo "ehci_hcd bus $bus: device $dev = $idVendor:$idProduct"
            done
            popd > /dev/null
    done
    popd > /dev/null
    ```
    
    The information is also usually available in /var/log/kern.log
-   Unbind the bus (and all devices) from the ehci\_hcd driver. Insert the bus id in the following command, using the format 0000:00:xx.x
    
    ```
     sudo sh -c 'echo -n "0000:00:xx.x" > unbind'
    ```
    

## Buffer I/O Errors

If you see errors related to Buffer I/O when attaching a USB storage device, there are two ways to work around it. First, try using varying max\_sectors settings, as such:

```
sudo sh -c "echo 120 > /sys/block/sda/queue/max_sectors_kb"
```

Try values of 120, 64 and 32.

If this does not resolve the issue, then you may need an unusual\_dev entry for your device. It would look something like this:

```
UNUSUAL_DEV(0x03eb , 0x2002, 0x0100, 0x9999,
            "Generic",
            "MusicDrive",
            US_SC_DEVICE, US_PR_DEVICE, NULL,
            US_FL_IGNORE_RESIDUE),
```

The vendor and device IDs can be obtained from the output of "lsusb". The entry would be placed in drivers/usb/storage/unusual\_devs.h. If you cannot compile your own kernel, please file a bug report, and we'll attempt to compile a test module for you.

## Device suddenly becomes read-only

If your device changes suddenly to read-only mode, and you see this kind of error:

```
[17183798.908000] FAT: Filesystem panic (dev sda1)
[17183798.908000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17183798.908000]     File system has been set read-only
```

This might be the sign of an unclean device. You should check your device. Try [TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia) to do so. Or use "Disk Utility" (under System, Administration), find your device, unmount it, check the file system, then mount it again.

## USB-Device is or becomes read-only without errors

If you see "Write Protect is off" and no errors in your logfiles, than you should set filesystem type specific mount options (FS\_MOUNTOPTIONS) in /etc/usbmount/usbmount.conf. Wrong gid causes mounting read only.

## General tip

When you encounter problems with USB devices, the first thing to do is to check the latest debug information generated from the kernel just after you plug in your device and/or just after you encounter the problem.  
To do that, open a terminal and type :

```
dmesg
```

Check the latest messages; they should be related to your problem.

## Seeking Further Help

The best place to get help with almost any Ubuntu problem is on the [Ubuntu Forums](http://ubuntuforums.org/). The _Absolute Beginner Talk_ section is best for beginners.

## Other Resources

![IconsPage/resources.png](https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=resources.png "IconsPage/resources.png")

  
Some other related material:  
  

-   [RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
    
-   [BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
    
-   [UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)
    
-   [http://en.wikipedia.org/wiki/USB\_flash\_drive](http://en.wikipedia.org/wiki/USB_flash_drive)
    
-   [DebuggingUSBStorage](https://help.ubuntu.com/community/DebuggingUSBStorage)
    

___

[CategoryHardware](https://help.ubuntu.com/community/CategoryHardware) [CategoryUsb](https://help.ubuntu.com/community/CategoryUsb)