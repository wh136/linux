# linux

全国大屏redis容器内/usr/local/bin/docker-entrypoint.sh

    #!/bin/sh
    set -e

    # first arg is `-f` or `--some-option`
    # or first arg is `something.conf`
    if [ "${1#-}" != "$1" ] || [ "${1%.conf}" != "$1" ]; then
            set -- redis-server "$@"
    fi

    # allow the container to be started with `--user`
    if [ "$1" = 'redis-server' -a "$(id -u)" = '0' ]; then
            chown -R redis .
            exec su-exec redis "$0" "$@"
    fi

    exec "$@"
    
    set命令用于设置shell, 只有添加参数后才能设置，并且在shell中输入set可以看到各种环境变量
    /usr/local/bin # set
    HISTFILE='/root/.ash_history'
    HOME='/root'
    HOSTNAME='dc3729b779e7'
    IFS=' 	
    '
    OLDPWD='/usr/local'
    OPTIND='1'
    PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'
    PPID='0'
    PS1='\w \$ '
    PS2='> '
    PS4='+ '
    PWD='/usr/local/bin'
    REDIS_DOWNLOAD_SHA='df4f73bc318e2f9ffb2d169a922dec57ec7c73dd07bccf875695dbeecd5ec510'
    REDIS_DOWNLOAD_URL='http://download.redis.io/releases/redis-4.0.9.tar.gz'
    REDIS_VERSION='4.0.9'
    SHLVL='1'
    TERM='xterm'
    _='docker-entrypoint.sh'

    
    set -e
    "Exit immediately if a simple command exits with a non-zero status."
    "set -e"之后出现的代码，一旦出现了返回值非零，整个脚本就会立即退出
    
