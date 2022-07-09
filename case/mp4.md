```
@echo off & setlocal enabledelayedexpansion
color 0a
echo ts2mp4
for %%a in ("*.ts","*.mkv") do ffmpeg -i "%%~a" -codec copy -f mp4 "%%~na.mp4"
echo delete .ts .mkv files?
pause
del *.ts,*.mkv
```