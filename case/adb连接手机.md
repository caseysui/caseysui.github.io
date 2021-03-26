### adb连接手机.bat
```
@echo off
:loop_start
echo.
echo 1.连接手机
echo.
echo 2.端口占用
echo.
echo 3.断开连接
set /p choice=输入序号：
IF NOT "%choice%"=="" SET choice=%choice:~0,1%
if /i "%choice%"=="1" goto set1_start
if /i "%choice%"=="2" goto set2_start
if /i "%choice%"=="3" goto set3_start
if /i "%choice%"=="4" goto set4_start
if /i "%choice%"=="5" goto set5_start
if /i "%choice%"=="6" goto set6_start
if /i "%choice%"=="7" goto set7_start
if /i "%choice%"=="8" goto set8_start
if /i "%choice%"=="9" goto set9_start
if /i "%choice%"=="0" goto set0_start
echo 重新输入
echo.
goto loop_start

:set1_start
echo 通过数据线连接手机
pause
echo 查看手机ip地址
adb shell ifconfig|findstr Bcast
adb shell ifconfig wlan0
set /p ip=输入手机ip地址192.168.
adb tcpip 5555
echo 断开手机数据线连接
pause
adb connect 192.168.%ip%
adb devices
echo DONE
goto endd

:set2_start
adb nodaemon server
netstat -ano | findstr "5037"
set /p a=输入进程PID
tasklist | findsty "%a%"
taskkill /f /pid %a%
echo DONE
goto endd

:set3_start
set /p ip=ip: 
adb disconnect 192.168.%ip%
echo Done
goto endd

:endd
echo.
pause
cls
goto loop_start
```

### 其他命令
```
传输文件
adb push <local> <remote>
adb push *.apk /sdcard/Download/
adb pull /sdcard/Download/*.apk

删除文件或目录
adb shell rm [-r] [-i] <files or directory>
adb shell rm -r -i /sdcard/Download/*.apk
-r	强制删除指定目录中的所有文件和子目录
-i	交互式删除，删除前提示

安装应用
adb install-multiple -r -d *.apk
-r	允许覆盖安装
-d	允许降级覆盖安装

卸载应用
adb uninstall <package-name>

关闭
adb kill-server

开启
adb start-server

查看所有应用
adb shell pm list packages > list.txt

查看系统应用
adb shell pm list packages -s > list.txt

查看第三方应用
adb shell pm list packages -3 > list.txt

包名包含某字符串的应用
adb shell pm list packages *** > list.txt

清除应用数据与缓存
adb shell pm clear <package-name>

强制停止应用
adb shell am force-stop <packagename>

查看前台活动
adb shell "dumpsys activity | findstr mResumedActivity"

查看正在运行的 Services
adb shell dumpsys activity services [<package-name>] > list.txt

查看应用详细信息
adb shell dumpsys package <package-name> >list.txt

查看应用安装路径
adb shell pm path <package-name>

启动应用调起 Activity
adb shell am start <intent>

点亮屏幕
adb shell input keyevent 224

熄灭屏幕
adb shell input keyevent 223

截图
adb shell screencap -p /sdcard/Download/test.png

录屏
adb shell screenrecord /sdcard/Download/test.mp4

输出设备信息到文件
adb shell getprop > info.txt

获取IMEI：
adb shell dumpsys iphonesubinfo

获取手机品牌：
adb shell getprop ro.product.brand

获取手机型号：
adb shell getprop ro.product.model

获取手机系统SDK版本号：
adb shell getprop ro.build.version.sdk

获取Android系统版本号：
adb shell getprop ro.build.version.release

获取手机分辨率：
adb shell wm size

获取手机dpi：
adb shell wm density

获取手机cpu架构：
adb shell getprop ro.product.cpu.abilist

获取手机mac：
adb shell cat /sys/class/net/eth0/address(网卡)

adb shell cat /sys/class/net/wlan0/address(无线网卡)

获取deviceId：
adb shell settings get secure android_id
```