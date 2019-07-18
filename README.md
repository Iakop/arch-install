#Arch Install Scripts

This is a collection of scripts that I will be using to install Arch Linux on my personal computer.
All of the scripts have been tested on a virtual machine, but should be able to run just as well on bare metal.
That being said, this is all a work in progress, and as such is not fully usable yet, without any human intervention.

List of todos:
- Connect to internet. Set clock.
- Detect whether UEFI or legacy BIOS boot is to be installed. 
- Detect hardware: RAM, disks, graphics
- From this info, perform the correct drive formatting in script.
	- Scaling the drive partitions with regards to RAM and swap needs (generally swap = 2xRAM)
	- Generate the partition from size and boot requirements
	- Mount
	- Generate fstab
- Pacstrap base, base-devel and my custom package list.
- Does arch-chroot work in script?
- Detect graphics, prompt user for driver installation:
	- TBD, whether to include bumblebee for NVidia or not.
	- Install graphics driver.
- Set the timezone, locale and vconsole keyboard settings.
- Prompt user for hostname, username, password, root password.
- Generate initramfs
- Install bootloader (for now, grub)
	- Maybe in the future, support adding an entry in existing bootloader.

That covers the basic setup, and from then on, I will script all my ricing as well.
This is intended to install everything from scratch, but perhaps the ricing scripts will be able to branch out from this project if they can be separated well enough.
