##CMD实用命令
```
###重命名
ren "*.txt" "*.bat"
ren "?A*.txt" "?B*.txt"

###批量获取文件名
dir *.* /b/s -n > list.txt
/s 包括该目录和子目录下的文件
/b 包括完整目录名
/a 包括隐藏文件
/ad 只显示文件夹名
-n 按字母排序
-d 按时间排序
-e 按扩展名排序
-s 按文件大小排序
新建或覆盖 >
追加文件名 >>

###提取当前目录下所有文件到指定目录，或当前目录（留空）
for /f "delims=" %a in ('dir /b/s -n *.*') do copy /-y "%a" D:\Downloads\

###删除文件名中的字符串
如需包括子文件，dir命令加上/s 参数
@echo off & setlocal enabledelayedexpansion
echo 删除空格
for /f "delims=" %%i in ('dir /b *.*') do (
    set "var=%%~nxi"
    set var=!var: =!
    ren "%%~fi" "!var!"
)
echo DONE
pause
echo 删除字符串
set /p a=输入要删除的字符串：
for /f "delims=" %%i in ('dir /b *%a%*') do (
set var=%%i
set var=!var:%a%=!
echo %%i to !var!
pause
ren "%%i" "!var!"
)
echo DONE
pause

```