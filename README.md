# Pi-star-GUI
Script to install a GUI and WebBrowser on Pi-Star
## Orignal for ideas written by Andy Taylor (MW0MWZ)
MMDVM热点安装微雪7寸IPS电容触控屏1024×600像素（DSI通信）后通过系统更新可以改为图形化界面。
使用步骤
首先SSH登陆后开启读写保护并取得管理权，然后扩展SD卡的空间
rpi-rw
sudo pistar-expand
扩展空间后需要重新启动系统
sudo reboot
然后利用wget命令取得安装脚本
#原始安装脚本
wget http://pistar.uk/downloads/installGUI.sh
#修改后的安装脚本
wget https://github.com/corallibra/Pi-star-GUI/blob/main/installGUI.sh
改变下载文件权限
chmod 755 installGUI.sh
运行该脚本
./installGUI.sh
安装脚本执行时间较长，完成后会重新启动系统，进入仪表板。
如果顺利进入仪表板，需要SSH登陆，或通过仪表板专家模式的终端窗口完成pi-star文件编辑。
sudo nano /etc/nginx/sites-enabled/pi-star
在文中找到”location ^~ /admin {“语句
另起一行，粘贴如下内容
satisfy any;
allow 127.0.0.1;
然后保存退出。
