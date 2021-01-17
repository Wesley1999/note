# 下载fancyindex
```
git clone https://github.com/aperezdc/ngx-fancyindex.git ngx-fancyindex
```

# 编译nginx
```
./configure --add-module=../ngx-fancyindex  [extra desired options]
make
```
用`./obj/nginx`替换原来的`nginx`

# 配置
vim nginx.conf
```
server {
	listen                  443 ssl;
	server_name             download.wangshaogang.com;
	root                    /oss/file;
	fancyindex            on;
	fancyindex_exact_size off;
	fancyindex_localtime  on;
	charset utf-8;
	error_page 403 404 500 502 503 504      /404;
	location = /404 {
		proxy_pass      https://404.wangshaogang.com/;
	}
	location /Nginx-Fancyindex-Theme/ {
		root /root/nginx/conf;
	}
}
```
详细配置参考下面的Reference

# 使用主题
我使用的主题：
```
https://github.com/Wesley1999/Nginx-Fancyindex-Theme/
```

```
fancyindex_header "/Nginx-Fancyindex-Theme/light-Theme/header.html";
fancyindex_footer "/Nginx-Fancyindex-Theme/light-Theme/footer.html";
```


# Reference
https://www.nginx.com/resources/wiki/modules/fancy_index/
http://www.ttlsa.com/nginx/nginx-module-ngx-fancyindex/
https://lanffy.github.io/2017/12/27/Nginx-Browse-Folder-Config