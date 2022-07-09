```
@echo off
mode con cols=50 lines=20 & color 0a
echo ================================================
echo			代理切换
echo ================================================
echo.
echo			1.局域网代理
echo.
echo			2.本机代理
echo.
echo			3.清空代理
echo.
:loop_start
set /p choice= 请输入：
IF NOT "%choice%"=="" SET choice=%choice:~0,1%
if /i "%choice%"=="1" goto set1_start
if /i "%choice%"=="2" goto set2_start
if /i "%choice%"=="3" goto set3_start
echo.
echo WTF???
echo.
goto loop_start

:set1_start
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /d "192.168.137.1:10803" /f
echo.
goto endd

:set2_start
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /d "127.0.0.1:10801" /f
echo.
goto endd

:set3_start
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v AutoConfigURL /d "" /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 0 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /d "" /f
echo.
goto endd

:endd
:closee
```

