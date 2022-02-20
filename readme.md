# PHP 7.2 with Apache Web server on docker

## Installed applications and libraries
- mcrypt
- vim
- wget
- curl
- unzip
- bc
- mc
- htop
- tmux
- sysstat
- iotop
- apg
- git
- subversion
- redis-tools
- imagemagick
- wkhtmltopdf
- sendmail
- ffmpeg
- composer
- psysh
- apache

## Installed php extensions
- mcrypt
- iconv
- exif
- gd
- pgsql
- mysql
- xml
- zip
- mbstring
- soap
- xdebug
- xhprof


## Edit /etc/hosts on host machine

```
127.0.0.1 xhprof.local
```

## Run xhprof profiler from the php code

##### start

```php
include_once "/usr/local/lib/php/xhprof_lib/utils/xhprof_lib.php";
include_once "/usr/local/lib/php/xhprof_lib/utils/xhprof_runs.php";
xhprof_enable(XHPROF_FLAGS_CPU + XHPROF_FLAGS_MEMORY);
```

``` debug code ```

##### finish
```php
(new \XHProfRuns_Default)->save_run(xhprof_disable(), "test");
```

How to configure PhpStorm + Xdebug + docker [article (ru)](https://blog.denisbondar.com/post/phpstorm_docker_xdebug)

[DockerHub](https://hub.docker.com/r/benms/php-apache-dev)
