```
@echo off
mode con cols=50 lines=20 & color 0a
echo BasicAuthLevel...
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters" /v BasicAuthLevel /t REG_DWORD /d 2 /f
echo.
echo FileSizeLimitInBytes...
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters" /v FileSizeLimitInBytes /t REG_DWORD /d 4294967295 /f
echo.
net stop webclient
net start webclient
echo Done
pause
```
