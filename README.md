# Linux on the RCA Cambio 10.1 Tablet

![alt text](https://github.com/lcashdol/rca-cambio-linux/raw/master/images/IMG_3982.jpg "Picture of RCA Cambio tablet")

# Distro support

Generally any Linux distribution will work with some alteration. Very few
distros currently work out of the box on this tablet due to the use of a 32
bit firmware on an amd64 Atom CPU.

- Debian (using [mixed mode](https://cdimage.debian.org/mirror/cdimage/release/9.0.0/multi-arch/iso-cd/ "Mixed mode ISO"))
- Ubuntu (using Linuxium's [isorespin.sh](http://linuxiumcomau.blogspot.com.au/2017/06/customizing-ubuntu-isos-documentation.html))
`
# ./isorespin.sh -i ubuntu-18.04.4-desktop-amd64.iso --atom
Extracting ISO ...
Parallel unsquashfs: Using 8 processors
141272 inodes (160595 blocks) to write

[================================================================/] 160595/160595 100%

created 113789 files
created 17309 directories
created 27449 symlinks
created 7 devices
created 0 fifos
Extracting isorespin files ...
Adding 32-bit GRUB packages ...
E: Version '2.02-2ubuntu8.14' for 'grub-efi-ia32' was not found
E: No packages found
E: Version '2.02-2ubuntu8.14' for 'grub-efi-ia32-bin' was not found
E: No packages found
Installing local packages ...
Adding files/directories ...
Running commands ...
Processing bootloader/bootmanager ...
Spinning ISO ...
Parallel mksquashfs: Using 8 processors
Creating 4.0 filesystem on iso-directory-structure/casper/filesystem.squashfs, block size 131072.
[================================================================\] 137748/137748 100%

Exportable Squashfs 4.0 filesystem, gzip compressed, data block size 131072
	compressed data, compressed metadata, compressed fragments, compressed xattrs
	duplicates are removed
Filesystem size 2099209.33 Kbytes (2050.01 Mbytes)
	44.01% of uncompressed filesystem size (4770060.49 Kbytes)
Inode table size 1654242 bytes (1615.47 Kbytes)
	26.91% of uncompressed inode table size (6146822 bytes)
Directory table size 1624458 bytes (1586.38 Kbytes)
	41.43% of uncompressed directory table size (3920994 bytes)
Xattr table size 46 bytes (0.04 Kbytes)
	38.33% of uncompressed xattr table size (120 bytes)
Number of duplicate files found 14106
Number of inodes 161785
Number of files 116971
Number of fragments 7559
Number of symbolic links  27457
Number of device nodes 7
Number of fifo nodes 0
Number of socket nodes 0
Number of directories 17350
Number of ids (unique uids + gids) 34
Number of uids 12
	root (0)
	dnsmasq (108)
	hplip (118)
	speech-dispatcher (111)
	systemd-network (100)
	syslog (102)
	_apt (104)
	man (6)
	colord (117)
	avahi-autoipd (106)
	gdm (121)
	geoclue (119)
Number of gids 26
	root (0)
	dip (30)
	shadow (42)
	ssl-cert (110)
	nogroup (65534)
	audio (29)
	systemd-network (102)
	utmp (43)
	tty (5)
	crontab (105)
	mlocate (109)
	ssh (115)
	messagebus (107)
	mail (8)
	staff (50)
	lpadmin (116)
	man (12)
	whoopsie (117)
	syslog (106)
	avahi-autoipd (112)
	colord (123)
	gdm (125)
	geoclue (124)
	adm (4)
	lp (7)
	systemd-journal (101)
xorriso 1.4.8 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev 'stdio:../../linuxium-atom-ubuntu-18.04.4-desktop-amd64.iso'
Media current: stdio file, overwriteable
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data,  550g free
xorriso : WARNING : -volid text problematic as automatic mount point name
xorriso : WARNING : -volid text is too long for Joliet (24 > 16)
xorriso : WARNING : -volid text does not comply to ISO 9660 / ECMA 119 rules
Added to ISO image: directory '/'='/home/larry/files/rca/isorespin/iso-directory-structure'
xorriso : UPDATE : 679 files added in 1 seconds
xorriso : UPDATE : 679 files added in 1 seconds
xorriso : NOTE : Copying to System Area: 512 bytes from file '/home/larry/files/rca/isorespin/isohdpfx.bin'
libisofs: WARNING : Cannot add /dists/stable to Joliet tree. Symlinks can only be added to a Rock Ridge tree.
libisofs: WARNING : Cannot add /dists/unstable to Joliet tree. Symlinks can only be added to a Rock Ridge tree.
libisofs: WARNING : Cannot add /ubuntu to Joliet tree. Symlinks can only be added to a Rock Ridge tree.
libisofs: NOTE : Automatically adjusted MBR geometry to 1020/136/32
libisofs: NOTE : Aligned image size to cylinder size by 150 blocks
xorriso : UPDATE :  1.86% done
xorriso : UPDATE :  21.93% done
xorriso : UPDATE :  36.91% done, estimate finish Thu May 14 19:25:10 2020
xorriso : UPDATE :  45.91% done, estimate finish Thu May 14 19:25:11 2020
xorriso : UPDATE :  52.70% done, estimate finish Thu May 14 19:25:11 2020
xorriso : UPDATE :  58.87% done, estimate finish Thu May 14 19:25:12 2020
xorriso : UPDATE :  64.96% done, estimate finish Thu May 14 19:25:13 2020
xorriso : UPDATE :  71.04% done, estimate finish Thu May 14 19:25:14 2020
xorriso : UPDATE :  77.03% done, estimate finish Thu May 14 19:25:14 2020
xorriso : UPDATE :  83.29% done, estimate finish Thu May 14 19:25:14 2020
xorriso : UPDATE :  89.47% done, estimate finish Thu May 14 19:25:15 2020
xorriso : UPDATE :  95.65% done
ISO image produced: 1109760 sectors
Written to medium : 1109760 sectors at LBA 0
Writing to 'stdio:../../linuxium-atom-ubuntu-18.04.4-desktop-amd64.iso' completed successfully.

isorespin.sh: Respun ISO created as 'linuxium-atom-ubuntu-18.04.4-desktop-amd64.iso' ... see logfile 'isorespin.log' for details.


# dd if=linuxium-atom-ubuntu-18.04.4-desktop-amd64.iso of=/dev/sdc bs=4M`


- Void (needs custom ISO)

  Need to create the custom ISO with Void's mklive and
  [PR102](https://github.com/voidlinux/void-mklive/pull/102)

- OpenBSD, not a Linux distro but includes support for bootia32.efi on the
  install media (install61.fs).

# Hardware

- 00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
- 00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
- 00:03.0 Multimedia controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Camera ISP (rev 0f)
- 00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
- 00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
- 00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)

Linux larry-W101-V2-TH2 5.3.0-51-generic #44~18.04.2-Ubuntu SMP Thu Apr 23 14:27:18 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

# Configuration

By default the RCA Cambio runs in portrait mode, but before booting you'll want
to add `video=efifb fbcon=rotate:1` to your kernel command line.

I needed to set `vga=normal` to disable the frame buffer on boot.

Linux Kernel 4.11 and higher is needed for DRM video acceleration.

# Similar pages

- [Install Linux on Nextbook Flexx Baytrail tablet](https://github.com/burzumishi/linux-baytrail-flexx10)

