## letsencrypt生成免费ssl证书及nginx配置支持https的方法

#### letsencrypt更新
git clone https://github.com/letsencrypt/letsencrypt

#### 脚本
	./letsencrypt-auto certonly --webroot -w /data/front/www.bdxmx.com/ -d www.bdxmx.com -m hhslqj@126.com
	
#### nginx配置
```
server{
	listen       80;
        listen 443 ssl on;
        server_name  www.bdxmx.com;
        ssl_certificate /etc/letsencrypt/live/www.bdxmx.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/www.bdxmx.com/privkey.pem;
        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers  on;
}
```
注 ： 新生成证书之后需重启nginx后证书才会生效

#### 参考博客
https://blog.csdn.net/dancen/article/details/81311688

