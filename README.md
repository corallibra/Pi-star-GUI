# Pi-star-GUI  
Script to install a GUI and WebBrowser on Pi-Star  
## Orignal for ideas written by Andy Taylor (MW0MWZ)  
MMDVM熱點安裝微雪7寸IPS電容觸控屏1024×600像素（DSI通信）後通過系統更新可以改為圖形化界面。
使用步驟  
首先SSH登陸後開啟讀寫保護並取得管理權，然後擴展SD卡的空間  
rpi-rw  
sudo pistar-expand  
擴展空間後需要重新啟動系統  
sudo reboot  
然後利用wget命令取得安裝腳本  
#原始安裝腳本  
wget http://pistar.uk/downloads/installGUI.sh  
#修改後的安裝腳本  
wget https://github.com/corallibra/Pi-star-GUI/blob/main/installGUI.sh  
改變下載文件權限  
chmod 755 installGUI.sh  
運行該腳本  
./installGUI.sh  
安裝腳本執行時間較長，完成後會重新啟動系統，進入儀表板。
如果順利進入儀表板，需要SSH登陸，或通過儀表板專家模式的終端窗口完成pi-star文件編輯。
sudo nano /etc/nginx/sites-enabled/pi-star  
在文中找到”location ^~ /admin {“語句  
另起一行，粘貼如下內容  
satisfy any;  
allow 127.0.0.1;  
然後保存退出。

-------------------------------------------------------------------------------------  
如果屏幕需要旋轉，可以編輯config.txt，在文末添加一句  
sudo nano /boot/config.txt  

#Default Orientation  
display_rotate=0  
*Rotate 90° Clockwise  
display_rotate=3  
*Rotate 180°  
display_rotate=2  
*Rotate 270° Clockwise  
display_rotate=1  
----------------------------------------------------------------------------------------  
更新过程中如遇到掉电可能会出现unable to acquire the dpkg frontend lock提示，可暴力杀死此进程。  
sudo rm /var/cache/apt/archives/lock-frontend  
sudo rm /var/lib/dpkg/lock-frontend  
