### 快捷键
⌘⌥⇧⌃
⌘+⇧+. 显示隐藏文件
⌘+⇧+G 访达转到
### 控制台命令
创建目录 mkdir 目录名
创建文件 touch 文件名.扩展名
删除目录 rm -rf 目录名
删除文件 rm 文件名
隐藏文件 chflags hidden 文件名
取消隐藏文件 chflags nohidden 文件名
### 其他操作
- 终端启用代理
编辑文件	~/.zshrc
alias proxy='export all_proxy=http://127.0.0.1:1082'
alias unproxy='unset all_proxy'
执行命令使其生效	source ~/.zshrc
输入proxy开启代理，unproxy关闭代理
- 开启不带格式粘贴
系统-键盘-键盘快捷键-APP快捷键
新增'粘贴并匹配样式'并把快键设为Cmd+V
