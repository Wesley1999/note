# 安装
如果已经安装过，需要先卸载，相应命令在最后。

```shell
sudo apt-get install samba
```

# 配置
```shell
sudo vim /etc/samba/smb.conf
```

在最后加上
```
[alldir]
    path=/
    browseable = yes
    writable=yes
    public=yes
    valid users=root
```

还需要修改`[home]`结点下的配置
```
browseable = yes
read only = no
valid users = root
```

然后，添加用户
```shell
smbpasswd -a root
```
输入两次密码即可

# 启动
可以用下面的命令启动和停止
```shell
service smbd start
service smbd stop
service smbd restart
```
修改配置后需要重启服务

# Windows上的映射
![](https://oss-pic.wangshaogang.com/1596903653850-d5996d96-d2d8-47af-adcb-87658b4f3a95.png)

![](https://oss-pic.wangshaogang.com/1596904746954-1a33a450-11a7-4024-89ba-3fed4793cd4e.png)


# 卸载
samba的卸载可能会存在配置文件残留等问题，这可能会导致再次安装时配置文件无法生效，无法正常启动samba服务。建议使用下列命令来彻底卸载samba
```shell
sudo apt-get remove --purge samba* samba-* smb*
sudo apt-get autoremove
sudo apt-get install libwbclient0 --reinstall
```

# 补充
home之外的目录是无法访问的，但可以通过挂载到home中的目录的形式访问硬盘中的文件。

# Reference
https://keytoon9.github.io/keytoon9.github.io/2020/02/01/raspi-1/
https://blog.csdn.net/electrocrazy/article/details/61681227