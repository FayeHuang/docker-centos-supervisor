docker-centos-supervisor
=============

[Supervisor](http://supervisord.org/) : 在 container 內管理(啟動、停止）多個 process

使用方式
-------

1. 編輯 supervisord.conf，將要管理的 process 寫入這個檔案

    ```
[supervisord]
nodaemon=true
logfile=/tmp/supervisord.log
pidfile=/tmp/supervisord.pid
 
[program:sshd]
command=/root/ssh_init.sh
```

2. 執行 fayehuang/centos-supervisor docker image
 * 不指定 root login 密碼，預設密碼為 **changeme**
 
    `docker run -d -p 2222:22 fayehuang/centos-supervisor`
 * 指定 root login 密碼，**ROOTPASSWORD**=mypassword
 
    `docker run -d -p 2222:22 -e ROOTPASSWORD=<mypassword> fayehuang/centos-supervisor`
