# pip安装配置

## python2安装pip
下载get-pip.py
https://oss-file.wangshaogang.com//script/get-pip.py
```
python get-pip.py
```

## 配置环境变量
Windows下同时配置python2、python3、pip2、pip3环境变量

把python3对应的python.exe、pip.exe重命名为python3.exe、pip3.exe即可

## pip换源
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```