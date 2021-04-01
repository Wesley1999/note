# 安装配置php
```shell
# 更新源
rpm -Uvh https://mirrors.cloud.tencent.com/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

# 安装PHP7.2
yum -y install mod_php72w.x86_64 php72w-cli.x86_64 php72w-common.x86_64 php72w-mysqlnd php72w-fpm.x86_64
# 安装mbstring扩展
yum install -y php-mbstring php-mcrypt php-gd

# 启动服务
systemctl start php-fpm
systemctl enable php-fpm
```

修改上传文件大小限制
```shell
vim /etc/php.ini

# 修改 upload_max_filesize

systemctl restart php-fpm
```







# 安装wordporess

下载
```shell
cd
wget https://cn.wordpress.org/latest-zh_CN.tar.gz
tar -zxvf latest-zh_CN.tar.gz -C /usr/local
```

配置Wordpress
```shell
# cd /usr/local/
# chmod 775 wordpress
cd /usr/local/wordpress
chmod -R 777 wp-content
cp wp-config-sample.php wp-config.php
vim wp-config.php
# 修改DB_NAME、DB_USER、DB_PASSWORD、DB_HOST
```

配置Nginx
```shell
    server {
        listen       443 ssl;
        server_name  test.wangshaogang.com;
        root         /usr/local/wordpress;
        #root         /root/docker/wordpress;
        location / {
            index index.php index.html index.htm;
        }
        location ~ \.php$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            # 设置脚本文件请求的路径
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            # 引入fastcgi的配置文件
            include        fastcgi_params;
        }
    }
```


https://cloud.tencent.com/document/product/213/38056
https://cloud.tencent.com/document/product/213/8044