Для запуска веб-приложения необходимо создать два конфигурационных файла:

_.../etc/systemd/system/fastapp.service_

```
[Unit]
Description=WebServer on FastAPI
After=network.target

[Service]
User=root
WorkingDirectory=/root/old_bot
ExecStart=/root/old_bot/venv/bin/uvicorn main:app --host 127.0.0.1 --port 8000
Restart=always

[Install]
WantedBy=multi-user.target
```

_.../etc/nginx/nginx.conf_

```
worker_processes 2;
user www-data;

events {
	use epoll;
	worker_connections 1024;
}


http {
	server_tokens off;
	include mime.types;
	charset utf-8;

    	server {
		listen 80;
		server_name miemproject1430.ru;

		location / {
			proxy_pass http://127.0.0.1:8000;
			proxy_set_header Host $host; 
			proxy_set_header X-Real-IP $remote_addr; 
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		}
	}
}
```
