```
重命名
ren "*.txt" "*.bat"
ren "?A*.txt" "?B*.txt"

批量获取文件名
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

提取当前目录下所有文件到指定目录，或当前目录（留空）
for /f "delims=" %a in ('dir /b/s -n *.*') do copy /-y "%a" D:\Downloads\
for /f "delims=" %a in ('dir /b/s -n *.*') do move /-y "%a" D:\Downloads\
```
