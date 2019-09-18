# Arch Install Scripts

This is a collection of scripts that I will be using to install Arch Linux on my personal computer.
All of the scripts have been tested on a virtual machine, but should be able to run just as well on bare metal.
That being said, this is all a work in progress, and as such is not fully usable yet, without any human intervention.

List of todos:

- Set up an ftp server on local machine. &#x2713;
- Connect to internet. &#x2713;
- Detect whether UEFI or legacy BIOS boot is to be installed. &#x2713;
- Set clock. &#x2713;
- Detect hardware: RAM, disks, graphics. &#x2713;
	- Pick disk to install on. &#x2713;
	- Add bumblebee to PRIME setups.&#x2713;
	- Added drivers to their own install list. &#x2713;
- From this info, perform the correct drive formatting in script. &#x2713;
	- Scaling the drive partitions with regards to RAM and swap needs (generally swap = 2xRAM) &#x2713;
	- Generate the partition from size and boot requirements &#x2713;
	- Mount &#x2713;
- Got arch-chroot working with a sub-script to run from the new root.&#x2713;
- Pacstrap base &#x2713;
	- Generate fstab &#x2713;
- Set the timezone, locale and vconsole keyboard settings. &#x2713;
- Get pacman mirrorlist and enable settings. &#x2713;
	- Add ILoveCandy and Color to pacman config (HEY! THAT'S HOW I LIKE IT!) &#x2713;
	- Enable multilib. &#x2713;
	- Add sublimetext repo for dev-version. &#x2713;
- Prompt user for hostname, username, password, root password. &#x2713;
- Install the packages specified in packages.list. &#x2713;
	- Install the graphics drivers mentioned in their install list. &#x2713;
	- Build and install pikaur. &#x2713;
	- Add keys to AUR user keyring. &#x2713;
	- Run pikaur to install aur-packages.list. &#x2713;
- Add configuration scripts to the applications that need them. &#x2713;
	- avahi &#x2713;
	- bluez &#x2713;
	- iptables &#x2713;
	- ufw &#x2713;
	- imagemagick &#x2713;
	- networkmanager &#x2713;
	- openssh &#x2713;
	- bumblebee &#x2713;
	- xorg (keyboard) &#x2713;
- Add systemwide mime-app definitions for: &#x2713;
	- feh &#x2713;
	- vim &#x2713;
- Add user configurables: &#x2713;
	- dotfiles &#x2713;
- Add linuxscripts to installer &#x2713;
- Generate initramfs &#x2713;
- Install bootloader &#x2713;
	- BIOS &#x2713;
	- UEFI &#x2713;
- Add check for CPU, to select microcode packages &#x2713;

**CONGRATULATIONS, THE INSTALLER INSTALLS A WHOLE SYSTEM**
___
**You are here:**
- Implement check for different versions of Nvidia drivers
	- If the card is old, install nouveau instead!
___

___
*Nice to haves*
- Sort in installed AUR packages, in general avoid:
	- Packages with poor architecture support.
		- Fix the build of compton-tryone-git for i386 (and pentium 4)
		- Maybe include packages pre-built
	- Huge compile-times.
		- purr-data
		- citra-canary-git
- Change hostname setting to use hostnamectl
- Implement choice of bootloader.
	- Between GRUB and rEFInd, if available
- Sort in installed packages, avoid using groups that bloat the system.
	- Groups to sort:
		- xorg
		- xorg-apps
	- (Maybe)
		- base
		- base-devel
- Configure retroarch correctly, and include the retroarch configuration in the configscripts.
___

This is intended to install everything from scratch, but perhaps the ricing scripts will be able to branch out from this project if they can be separated well enough.

An easy way to develop the script outside of a VM, and pull the changes into the VM, is to set up an FTP server on the host machine, and pull the changes through wget in a small script. The script I have made is `ftphack`. It needs as a minimum the host machine's ip in `/etc/hosts` like so, for example:

```bash
[ip address]	[hostname]
192.168.x.x	devpc
```

That should speed up development somewhat. Of course the script needs to be gotten on the VM first, but that should be simple through `wget` as well!
