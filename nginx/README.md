upstream django {
    server unix://run/uwsgi/eh34.sock;
}


server {
    listen      80;
    server_name 35.180.92.52;
    charset     utf-8;
    client_max_body_size 75M;

    location /media/  {
        root /home/ubuntu/projectEtanchHerault34/static/images/;
    }

    location /static/ {
        root /home/ubuntu/projectEtanchHerault34/;
    }

    location /staticfiles/ {
        root /home/ubuntu/projectEtanchHerault34/staticfiles/;
    }

    location / {
        uwsgi_pass  django;
        include     /home/ubuntu/projectEtanchHerault34/uwsgi_params;
    }   
}
