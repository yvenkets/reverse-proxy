If we make build and use 



server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
}

If we Run the backend in background

server {
        listen 80;
        listen [::]:80;

        root /var/www/node.venketraman.com/html;
        index index.html index.htm index.nginx-debian.html;

        server_name node.venketraman.com www.web.com;
	
	location /hello {
        proxy_pass http://localhost:9009;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        }

}
