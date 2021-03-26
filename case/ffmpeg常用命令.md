### ffmpeg常用命令
```
@echo off & setlocal enabledelayedexpansion
mode con cols=100 lines=30 & color 0a
:loop_start
echo  ===========================================
echo  		FFMPEG命令大全
echo  ===========================================
echo.
echo        		1.提取音频 
echo.		
echo        		2.调整音量
echo.		
echo        		3.提取视频
echo.		
echo        		4.合并
echo.		
echo        		5.视频格式转换
echo.		
echo        		6.视频转动画
echo.		
echo        		7.倒放
echo.		
echo        		8.批量截取视频（相同时长）
echo.		
echo        		9.批量截取视频（不同时长）

set /p choice=    请选择：
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
echo 请重新输入
echo.
goto loop_start
::====================================================================================

REM 提取音频 
:set1_start
for %%a in ("*.mp4") do ffmpeg -hide_banner -y -i %%a -vn -acodec copy "%%~na_ffmpeg.m4a"
REM for %%a in ("*.mp4") do ffmpeg -hide_banner -y -i %%a -vn -ar 44100 -acodec libmp3lame -b:a 320k "%%~na_ffmpeg.mp3"
echo.
goto endd

REM 提取视频
:set2_start
for %%a in ("*.mp4") do ffmpeg -hide_banner -y -i %%a -vcodec copy -an "%%~na_ffmpeg.mp4"
echo.
goto endd

REM 调整音量
:set3_start
REM ffmpeg -hide_banner -i test.mp3 -af "volumedetect" -f null /dev/null
for %%a in ("*.mp3") do ffmpeg -y -i %%a -af "volume=10dB" "%%~na_ffmpeg.mp3"
REM for %%a in ("*.mp3") do ffmpeg -y -i %%a -af "volume=2" "%%~na_ffmpeg.mp3"
echo.
goto endd

REM 合并
:set4_start
for %%a in ("*.mp4") do ffmpeg -hide_banner -y -i %%a -f mpegts -codec copy "%%~na_ffmpeg.ts"
for %%a in ("*.ts") do echo file '%%a' >> list.txt
ffmpeg -hide_banner -y -f concat -safe 0 -i list.txt -codec copy ffmpeg.mp4
del /q ""*.ts""
REM ffmpeg -hide_banner -y -i "concat:test1.mp4|test2.mp4" -codec copy ffmpeg.mp4
REM ffmpeg -hide_banner -y -i "concat:test1.mp3|test2.mp3" -codec copy ffmpeg.mp3
REM ffmpeg -hide_banner -y -i video1.mp4 -acodec copy -vn audio.m4a
REM ffmpeg -hide_banner -y -i video2.mp4 -vcodec copy -an video.mp4
REM ffmpeg -hide_banner -y -i video.mp4 -i audio.m4a -vcodec copy -acodec copy video_audio.mp4
echo.
goto endd

REM 视频格式转换
:set5_start
ffprobe -show_format test.mp4
for %%a in ("*.mp4",*.avi,"*.mkv") do ffmpeg -hide_banner -y -i %%a -crf 20 -preset slow -c:v libx264 -b:v 3500k -acodec copy "%%~na_ffmpeg.mp4"
REM 720P 3500k 1080P 8500k
echo.
goto endd

REM mp4转gif
:set6_start
for %%a in ("*.mp4") do ffmpeg -hide_banner -y -accurate_seek -ss 00:00:10.000 -to 00:00:20.000 -i %%a -vf scale=480:-1 -f gif -r 15 %%~na_ffmpeg.gif
echo.
goto endd

REM 倒放
:set7_start
REM 1.视频倒放，音频不变
ffmpeg -hide_banner -i test.mp4 -acodec copy -vf reverse ffmpeg_test.mp4
REM 2.音频倒放，视频不变
ffmpeg -hide_banner -i test.mp4 -vcodec copy -af areverse ffmpeg_test.mp4
REM 3.音视频同时倒放
ffmpeg -hide_banner -i test.mp4 -vf reverse -af areverse ffmpeg_test.mp4
echo.
goto endd

REM 批量截取视频1
:set8_start
REM -ss开始时间 -to 结束时间 -t 持续时间
for %%a in ("*.mp4") do ffmpeg -hide_banner -y -accurate_seek -ss 00:00:10.000 -to 00:00:20.000 -i %%a -codec copy -avoid_negative_ts 1 "%%~na_ffmpeg.mp4"
REM 精确截取视频，速度慢
REM for %%a in ("*.mp4") do ffmpeg -hide_banner -y -ss 00:00:10.000 -to 00:00:20.000 -i %%a -c:v libx264 -b:v 3500k -acodec copy "%%~na_ffmpeg.mp4"
echo.
goto endd

REM 批量截取视频2
:set9_start
@echo off & setlocal enabledelayedexpansion
set "s1=00:00:10.000"
set "s2=00:00:10.000"
for /f "tokens=1-4delims=:." %%a in ("%s2%") do (
    set /a "t2=(1%%a %% 100 *3600 + 1%%b %% 100 * 60 + 1%%c %% 100) * 1000 + 1%%d %% 1000"
)

md ffmpeg 2>nul
for %%a in (*.avi "*.mkv" "*.mp4" "*.flv") do (
    for /f "tokens=2-5delims=:., " %%a in ('ffmpeg -i "%%a" 2^>^&1 ^| find "Duration:"') do (
        set /a "t=(1%%a%%100*3600+1%%b%%100*60+1%%c%%100)*1000+1%%d0%%1000,t-=t2,ms=t%%1000,t/=1000"
        set /a h=t/3600,m=t%%3600/60,s=t%%60,h+=100,m+=100,s+=100,ms+=1000
        set "t=!h:~1!:!m:~1!:!s:~1!.!ms:~1!"
        ffmpeg -hide_banner -y -accurate_seek -ss !s1! -to !t!  -i "%%a" -codec copy -avoid_negative_ts 1 "ffmpeg\%%a"
    )
)
echo.
goto endd
::====================================================================================

:endd
pause
cls
goto loop_start
```