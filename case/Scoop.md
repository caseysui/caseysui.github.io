```
1. Install
set-executionpolicy remotesigned -scope currentuser
iwr -useb get.scoop.sh | iex
scoop config proxy 127.0.0.1:7890
scoop config proxy 192.168.137.1:7890
Set-ItemProperty 'HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem' -Name 'LongPathsEnabled' -Value 1
scoop install git
scoop install innounp
scoop install aria2
scoop install 7zip
scoop install ffmpeg
scoop install sudo
scoop install python
scoop config aria2-enabled true
scoop config aria2-enabled false
pip3 install --upgrade pip
pip3 install --upgrade you-get
pip3 install --upgrade youtube-dl

2. Update
scoop checkup
scoop reset *
scoop uninstall *
scoop update *
scoop update --all

3. Video download
you-get -x 127.0.0.1:7890 ""
youtube-dl -f best --proxy http://127.0.0.1:7890 ""
```