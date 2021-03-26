### ts转mp4批处理
```
@echo off & setlocal enabledelayedexpansion
echo ts转mp4
for "%%a" in ("*.ts") do ffmpeg -hide_banner -i "%%a" -f mp4 -vcodec copy -acodec copy "%%~na_ffmpeg.mp4"
echo 开始删除ts原始文件
del *.ts
echo 开始删除_ffmpeg后缀
for /f "delims=" %%i in ('dir /b *_ffmpeg*') do (
set var=%%i
set var=!var:_ffmpeg=!
echo %%i !var!
ren "%%i" "!var!"
)
echo DONE
pause
```