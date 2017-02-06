### nginx-tutor
nginx 默认的服务器根目录
`/usr/share/nginx/html`
配置文件在于
`/etc/nginx/nginx.conf`
平滑启动nginx
`nginx -s reload`
>  平滑启动的意思是在不停止nginx的情况下，重启nginx，重新加载配置文件，启动新的工作线程，完美停止旧的工作线程``

还有另外一种平滑启动的方法 
`kill -s QUIT 1628`
1628为nginx的pid，
> the nginx.pid in the directory /usr/local/nginx/logs or /var/run



> To start nginx, run the executable file. Once nginx is started, it can be controlled by invoking the executable with the -s parameter. Use the following syntax:
> 
> nginx -s signal
> Where signal may be one of the following:
> 
> stop — fast shutdown
> quit — graceful shutdown
> reload — reloading the configuration file
> reopen — reopening the log files

