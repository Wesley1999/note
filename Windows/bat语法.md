# bat语法

## 打开文件/目录
```
start "" "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
```



## 以管理员身份运行
例如以管理员身份用记事本打开host文件
```
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
cd /d "%~dp0"
notepad C:/Windows/System32/drivers/etc/hosts
```

## 解决中文乱码
用Notepad++打开，改成ANSI编码