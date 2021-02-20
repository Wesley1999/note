设置root密码

```shell
sudo passwd root
```

切换到root用户

```shell
su root
```

编辑ssh配置

```shell
vi /etc/ssh/sshd_config
```

`PasswordAuthentication no` 改为 `PasswordAuthentication yes`

重启sshd

```shell
service sshd restart
```

之后，就可以使用root用户名密码ssh登录
