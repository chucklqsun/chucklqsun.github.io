### How to install Facetime driver on Macbook Ubuntu
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

### Change Default Keyboard LED and Screen brightness
vi /etc/rc.local
echo 180 > /sys/class/backlight/gmux_backlight/brightness
echo 0 > /sys/class/leds/smc::kbd_backlight/brightness

### VirtualBox虚拟机xp里没有声音
1. 启动虚拟机里的声音AC97
2. 在client里安装驱动，可以从xp光盘或者vBox_NetAuto_Driver.iso里安装
3. 如果安装驱动后还没有声音，需要从服务里启动Windows Audio的管理服务

### 安装日式键盘
1. Linux很简单，直接选择Japanese(日文)键盘布局
2. Windows需要先更新键盘驱动成Japanese PS/2（列表里选择），然后添加键盘布局日语（日本）

### VirtualBox中Mac和Ubuntu共享文件夹权限问题
```
sudo adduser yourusername vboxsf
```
注销，然后重新进入桌面就可以访问了。

### 如果移动硬盘无法被载入进虚拟机
在setting里设置载入移动硬盘，并且检查是否使用了USB3.0。

## 递归文件夹并整理成树状结构
brew install tree
tree -I "__pycache__"   ## ignore folder __pycache__

## 进入恢复模式（安装系统，重新分区等用途）
Keyboard input: command + R

## 杀死chromedriver的残余进程
```
ps aux | grep chromedriver | awk '{print $2}' | xargs kill -9
```
