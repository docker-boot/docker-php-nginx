# PHP Nginx

网址
------
<pre>
http://公网ip:81

http://公网ip:82

http://公网ip:83
</pre>

81端口
------
<pre>
.../workspace/test
</pre>

进Nginx容器
------
<pre>
docker-compose exec nginx sh
</pre>

进PHP容器
------
<pre>
docker-compose exec php-fpm bash
</pre>

执行
------
<pre>
php -r "echo \"hello world\n\";"
</pre>
