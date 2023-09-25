### Accessing mother board booting option:
For MSI Pro Series press F11 when board logo appears. This should allow you to choose from all boot options.
Select install media if available.

When installing Ubuntu: 
Option 1 
![[Pasted image 20230924134833.png]]
And use slider to decide how much disk space to allocate
![[Pasted image 20230924135136.png]]
Option 2: 
![[Pasted image 20230924135258.png]]
Assign the entire boot disk to the install
Option 3:
![[Pasted image 20230924135450.png]]
And disk size manually set using installer
Option 4:
![[Pasted image 20230924153626.png]]
(The green segment on the side is the boot/EFI partition)
Install/Use Gparted in advance to create new partition. If you are using a live ISO you can still install software in it. Ubuntu came with it installed, however, to modify the root partition you should download 
Gparted live and install it on a USB stick because you can't do it while Ubuntu Live is using it.
![[Pasted image 20230924155044.png]]
Naming and resizing using Gparted Live. The Key is planning disk partition layout based on intended software use. I increasing the size is likely possible than leave space between partitions.

===Its recommended to write down what the EFI System partition name. e.g: /dev/sda1===  because you are going to need to give the installer the name of EFI partition as well as the name of the partition you to install the operating system e.g.: /dev/sda3. 
Always create ===EXT4=== partitions, the current standard for Linux.

On systems with smaller amounts of ram create a swap partition at the opposite end of the drive graph.

Once done partitioning, power off and remove media and insert install media. When installer begins, choose manual partition and