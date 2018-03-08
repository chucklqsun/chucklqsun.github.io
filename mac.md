# How to install Facetime driver on Macbook Ubuntu
[How to install Ubuntu 16.04 on Mac Pro][ref1]
```
$ cd /etc/local/src
$ git clone https://github.com/patjak/bcwc_pcie.git
$ cd bcwc_pcie/firmware
$ sudo make
$ sudo make install
$ cd ..
$ sudo make
$ sudo make install
$ sudo depmod
$ sudo modprobe -r bdc_pci
$ sudo modprobe facetimehd
```
[ref1]: https://medium.com/@racter/how-to-install-ubuntu-16-04-on-a-retina-macbook-11-2-74e7779c0e47 "How to Install Ubuntu 16.06 on Mac Pro"

# Change Default Keyboard LED and Screen brightness
sudo vi /etc/rc.local
echo 180 > /sys/class/backlight/gmux_backlight/brightness
echo 0 > /sys/class/leds/smc::kbd_backlight/brightness
setpci -v -H1 -s 00:01.00 BRIDGE_CONTROL=0
<**below code may need to be modified after each update**>
sudo vi /etc/default/grub
Change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
To:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=Linux"
```

# How to install Nvidia Driver
To disable the Nouveau kernel driver:
1. Remove the installed NVIDIA drivers:
```
$ sudo apt-get purge "nvidia*"
```
2. Create a new file named /etc/modprobe.d/disable-nouveau.conf with the following lines:
```
blacklist nouveau
options nouveau modeset=0
```
3. Update the boot environment for your kernel:
```
$ sudo update-initramfs -u
```
Now reboot and you should get a low resolution GUI which indicates that Nouveau graphics driver is not being used.
