```shell
vi /etc/sysconfig/network-scripts/ifcfg-enp4s0f0
```

ifcfg-enp4s0f0是网卡设备名。

修改以下配置：

```shell
NETMASK=255.255.255.0
NETWORK=192.168.1.0
IPADDR=12.168.1.117
ONBOOT=yes
```

重启网络服务：

```shell
service network restart
```