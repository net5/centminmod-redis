Info:
=======

Redis server generator to create multiple Redis servers locally listening on 127.0.0.1 with starting port `STARTPORT=6479` and incrementally created via integer passed on `redis-generator.sh` command line. Written for CentOS 7 only with [centminmod.com](https://centminmod.com) LEMP stacks specifically.

Usage:
=======

    ./redis-generator.sh
    
    Usage where X equal postive integer for number of redis
    servers to create with incrementing TCP redis ports
    starting at STARTPORT=6479
    
    ./redis-generator.sh X

Examples:
=======

With `DEBUG_REDISGEN='y'` for dry run debug run checks

    ./redis-generator.sh 1
    
    Creating redis servers starting at TCP = 6479...
    -------------------------------------------------------
    creating redis server: redis6479.service [increment value: 0]
    redis TCP port: 6479
    create systemd redis6479.service
    cp -a /usr/lib/systemd/system/redis.service /usr/lib/systemd/system/redis6479.service
    create /etc/redis6479.conf config file
    cp -a /etc/redis.conf /etc/redis6479.conf
    grep: /etc/redis6479.conf: No such file or directory
    sed -i "s|^port 6379|port 6479|" /etc/redis6479.conf
    sed -i 's|^daemonize no|daemonize yes|' /etc/redis6479.conf
    sed -i "s|pidfile \/var\/run\/redis_6379.pid|pidfile \/var\/run\/redis\/redis_6479.pid|" /etc/redis6479.conf
    sed -i "s|\/var\/log\/redis\/redis.log|\/var\/log\/redis\/redis6479.log|" /etc/redis6479.conf
    sed -i "s|dbfilename dump.rdb|dbfilename dump6479.rdb|" /etc/redis6479.conf
    sed -i "s|appendfilename "appendonly.aof"|appendfilename "appendonly6479.aof"|" /etc/redis6479.conf
    echo "#masterauth abc123" >> /etc/redis6479.conf
    sed -i "s|\/etc\/redis.conf|\/etc\/redis6479.conf|" /usr/lib/systemd/system/redis6479.service
    systemctl daemon-reload
    systemctl restart redis6479
    Redis TCP 6479 Info:
    redis-cli -h 127.0.0.1 -p 6479 INFO SERVER
    -------------------------------------------------------
    creating redis server: redis6480.service [increment value: 1]
    redis TCP port: 6480
    create systemd redis6480.service
    cp -a /usr/lib/systemd/system/redis.service /usr/lib/systemd/system/redis6480.service
    create /etc/redis6480.conf config file
    cp -a /etc/redis.conf /etc/redis6480.conf
    grep: /etc/redis6480.conf: No such file or directory
    sed -i "s|^port 6379|port 6480|" /etc/redis6480.conf
    sed -i 's|^daemonize no|daemonize yes|' /etc/redis6480.conf
    sed -i "s|pidfile \/var\/run\/redis_6379.pid|pidfile \/var\/run\/redis\/redis_6480.pid|" /etc/redis6480.conf
    sed -i "s|\/var\/log\/redis\/redis.log|\/var\/log\/redis\/redis6480.log|" /etc/redis6480.conf
    sed -i "s|dbfilename dump.rdb|dbfilename dump6480.rdb|" /etc/redis6480.conf
    sed -i "s|appendfilename "appendonly.aof"|appendfilename "appendonly6480.aof"|" /etc/redis6480.conf
    echo "#masterauth abc123" >> /etc/redis6480.conf
    sed -i "s|\/etc\/redis.conf|\/etc\/redis6480.conf|" /usr/lib/systemd/system/redis6480.service
    systemctl daemon-reload
    systemctl restart redis6480
    Redis TCP 6480 Info:
    redis-cli -h 127.0.0.1 -p 6480 INFO SERVER

With `DEBUG_REDISGEN='n'` for live run and generation of redis servers with X = 1 meaning create 2x redis servers on starting port `6479` and `6480` (port incremented by 1)

    ./redis-generator.sh 1  
    
    Creating redis servers starting at TCP = 6479...
    -------------------------------------------------------
    creating redis server: redis6479.service [increment value: 0]
    redis TCP port: 6479
    create systemd redis6479.service
    cp -a /usr/lib/systemd/system/redis.service /usr/lib/systemd/system/redis6479.service
    create /etc/redis6479.conf config file
    cp -a /etc/redis.conf /etc/redis6479.conf
    -rw-r----- 1 redis root 46K Mar 13 21:22 /etc/redis6479.conf
    -rw-r--r-- 1 root  root 249 Sep 14 08:43 /usr/lib/systemd/system/redis6479.service
    ## Redis TCP 6479 Info ##
    # Server
    redis_version:3.2.8
    redis_git_sha1:00000000
    redis_git_dirty:0
    redis_build_id:dd923e72e9efa6d8
    redis_mode:standalone
    os:Linux 3.10.0-514.10.2.el7.x86_64 x86_64
    arch_bits:64
    multiplexing_api:epoll
    gcc_version:4.8.5
    process_id:3915
    run_id:369baaef3d64b6f2324586c7f9de19d530e56b69
    tcp_port:6479
    uptime_in_seconds:0
    uptime_in_days:0
    hz:10
    lru_clock:13131760
    executable:/usr/bin/redis-server
    config_file:/etc/redis6479.conf
    -------------------------------------------------------
    creating redis server: redis6480.service [increment value: 1]
    redis TCP port: 6480
    create systemd redis6480.service
    cp -a /usr/lib/systemd/system/redis.service /usr/lib/systemd/system/redis6480.service
    create /etc/redis6480.conf config file
    cp -a /etc/redis.conf /etc/redis6480.conf
    -rw-r----- 1 redis root 46K Mar 13 21:22 /etc/redis6480.conf
    -rw-r--r-- 1 root  root 249 Sep 14 08:43 /usr/lib/systemd/system/redis6480.service
    ## Redis TCP 6480 Info ##
    # Server
    redis_version:3.2.8
    redis_git_sha1:00000000
    redis_git_dirty:0
    redis_build_id:dd923e72e9efa6d8
    redis_mode:standalone
    os:Linux 3.10.0-514.10.2.el7.x86_64 x86_64
    arch_bits:64
    multiplexing_api:epoll
    gcc_version:4.8.5
    process_id:3954
    run_id:9e5b98ca757acfc67e8ea9216943cf3fd3336970
    tcp_port:6480
    uptime_in_seconds:0
    uptime_in_days:0
    hz:10
    lru_clock:13131760
    executable:/usr/bin/redis-server
    config_file:/etc/redis6480.conf

```
systemctl status redis6479 
● redis6479.service - Redis persistent key-value database
   Loaded: loaded (/usr/lib/systemd/system/redis6479.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2017-03-14 21:28:37 UTC; 7s ago
  Process: 3985 ExecStop=/usr/libexec/redis-shutdown (code=exited, status=0/SUCCESS)
 Main PID: 4008 (redis-server)
   CGroup: /system.slice/redis6479.service
           └─4008 /usr/bin/redis-server 127.0.0.1:6479

Mar 14 21:28:37 host.domain.com systemd[1]: Started Redis persistent key-value database.
Mar 14 21:28:37 host.domain.com systemd[1]: Starting Redis persistent key-value database...
```

```
systemctl status redis6480
● redis6480.service - Redis persistent key-value database
   Loaded: loaded (/usr/lib/systemd/system/redis6480.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2017-03-14 21:26:08 UTC; 2min 56s ago
 Main PID: 3954 (redis-server)
   CGroup: /system.slice/redis6480.service
           └─3954 /usr/bin/redis-server 127.0.0.1:6480

Mar 14 21:26:08 host.domain.com systemd[1]: Started Redis persistent key-value database.
Mar 14 21:26:08 host.domain.com systemd[1]: Starting Redis persistent key-value database...
```