### 合并mp4
```
@echo off & setlocal enabledelayedexpansion
echo mp4转ts
for %%a in ("*.mp4") do ffmpeg -y -i "%%a" -f mpegts -codec copy "%%~na.ts"
echo ts合并成mp4
for %%i in ("*.ts") do echo file '%%i' >> list.txt
ffmpeg -y -f concat -safe 0 -i list.txt -c copy output.mp4
echo 删除ts文件
del -q "*.ts"
echo DONE
pause
```