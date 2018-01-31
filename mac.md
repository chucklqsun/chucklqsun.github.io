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
vi /etc/rc.local 
echo 180 > /sys/class/backlight/gmux_backlight/brightness
echo 0 > /sys/class/leds/smc::kbd_backlight/brightness
