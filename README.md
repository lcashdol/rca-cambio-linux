# Linux on the RCA Cambio 10.1 Tablet

![alt text](https://github.com/lcashdol/rca-cambio-linux/raw/master/images/IMG_3982.jpg "Picture of RCA Cambio tablet")

# Distro support

Generally any Linux distribution will work with some alteration. Very few
distros currently work out of the box on this tablet due to the use of a 32
bit firmware on an amd64 Atom CPU.

- Debian (using [mixed mode](https://cdimage.debian.org/mirror/cdimage/release/9.0.0/multi-arch/iso-cd/ "Mixed mode ISO"))
- Ubuntu (using Linuxium's [isorespin.sh](http://linuxiumcomau.blogspot.com.au/2017/06/customizing-ubuntu-isos-documentation.html))

./isorespin.sh -i ubuntu-18.04.4-desktop-amd64.iso --atom

dd if=linuxium-atom-ubuntu-18.04.4-desktop-amd64.iso of=/dev/sdc bs=4M


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

