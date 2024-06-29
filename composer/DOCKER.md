# PHP Composer - Docker

安装
------
<pre>
docker pull composer
</pre>

执行
------
<pre>
docker run --rm --interactive --tty --volume $PWD:/app composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

docker run --rm --interactive --tty --volume $PWD:/app composer install -vvv

docker run --rm --interactive --tty --volume $PWD:/app composer update -vvv
</pre>
