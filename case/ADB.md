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
adb uninstall --user0 <package-name>

禁止一加系统更新
adb shell pm disable-user com.oneplus.opbackup
adb shell pm clear com.oneplus.opbackup
adb shell pm enable com.oneplus.opbackup

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
adb shell dumpsys window w | findstr \/ | findstr name=

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