# Config uwsgi


### Create ini file

- create `appname.ini` file into folder `/etc/uwsgi/sites/`

after creating ini file put this content and customize

```
[uwsgi]
chdir           =/home/ubuntu/projectEtanchHerault34
module          =projectEtanchHerault34.wsgi:application
home            =/home/ubuntu/projectEtanchHerault34/.venv
max-requests    =1000
master          =true
processes       =5
uid		          =ubuntu
socket          =/etc/uwsgi/sites/appname.sock
socket-chmod    =660
vacuum          =true
# daemonize     =/var/log/uwsgi/appname.log
```


### Create systemd unit file for uWsgi

create ```uwsgi.service``` in ```/etc/systemd/system/```


after creating ini file put this content and customize

```
[Unit]
Description=uWSGI Emperor

[Service]
ExecStart=/home/ubuntu/.local/bin/uwsgi --emperor /etc/uwsgi/sites/appname.ini
RuntimeDirectory=uwsgi
Restart=always
KillSignal=SIGQUIT
Type=simple
NotifyAccess=all

[Install]
WantedBy=multi-user.target
```

### reload the service

```sudo systemct daemon-reload```

### start and stop uwsgi service

```sudo systemctl start uwsgi.service```

```sudo systemctl stop uwsgi.service```



### enable service to be start after reboot


```sudo systemctl enable uwsgi.service```





