# Arch Install Scripts

This is a collection of scripts that I will be using to install Arch Linux on my personal computer.
All of the scripts have been tested on a virtual machine, but should be able to run just as well on bare metal.
That being said, this is all a work in progress, and as such is not fully usable yet, without any human intervention.

List of todos:

- Set up an ftp server on local machine. &#x2713;
- Connect to internet. &#x2713;
- Detect whether UEFI or legacy BIOS boot is to be installed. &#x2713;
- Set clock. &#x2713;
- Detect hardware: RAM, disks. &#x2713;
	- Pick disk to install on. &#x2713;
___
**You are here:**
- From this info, perform the correct drive formatting in script.
	- Scaling the drive partitions with regards to RAM and swap needs (generally swap = 2xRAM)
	- Generate the partition from size and boot requirements
	- Mount
	- Generate fstab
___

- Detect hardware: Graphics.
- Pacstrap base, base-devel and my custom package list (Including package drivers!).
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

An easy way to develop the script outside of a VM, and pull the changes into the VM, is to set up an FTP server on the host machine, and pull the changes through wget in a small script (the name `ftphack` is already added in `.gitignore`, but **please** remember not to push your password and username!)

```bash
#!/bin/bash

# Remove any old versions:
rm arch-install
# wget the new version over ftp:
wget ftp://username:password@hostaddress/location/of/arch-install
# Ensure the new version is executable:
chmod 755 arch-install
```

That should speed up development somewhat. Of course the script needs to be gotten on the VM first, but that should be simple through `wget` as well!
