1. 
树莓派官网系统网址:https://www.raspberrypi.com/software/operating-systems/
在树莓派官网下载最新版本的镜像，将压缩文件下载到PC上，并解压得到.img文件。
2. 
TF卡连接到PC，使用SDFormatter软件格式化TF卡。
3. 
打开Win32DiskImager软件，选择第1步准备的系统镜像，点击write烧写系统镜像。
4.
烧录完成后，在我的电脑中会出现boot盘符，将JMO-DSI-LCD文件夹拷贝进去
5.
将TF卡接入到树莓派上，接上键盘和鼠标，并启动树莓派，登录树莓派的终端（可以将树莓派接到HDMI显示器或用ssh远程登录）。
6.
打开终端，输入命令uname -r查看当前内核版本,显示如下:
pi@raspberrypi:~ $ uname -r
5.15.61-v7l+
5.15.61即为内核版本， v7l字样则表示32位系统，如果是v8字样则表示64位系统

7.
在终端运行如下命令:
#cd JMO-DSI-LCD
#根据上述信息，进入32文件夹，如果是64位，则cd 64
#cd 32
#cd 5.15.61
接着是安装驱动，运行:
sudo ./JMO_7inchDSI1024x600_MAIN.sh
等待几秒钟，如果没有任何错误提示，即可加载驱动成功。

8.
sudo reboot重启机器即可点亮lcd屏 (有个别版本树莓派系统重启会卡住，需要重新断电上电)

9.
系统启动后调节背光亮度：
#先修改权限为可写:
#sudo chmod 777 /sys/class/backlight/rpi-backlight/brightness
#将亮度调节为100:
#echo 100 > /sys/class/backlight/rpi-backlight/brightness
#将亮度调到0:
#echo 0 > /sys/class/backlight/rpi-backlight/brightness
#将亮度调到最亮:
#echo 255 > /sys/class/backlight/rpi-backlight/brightness

