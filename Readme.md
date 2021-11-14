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

![image](https://user-images.githubusercontent.com/38104778/141679966-bde04ff7-c507-46d8-b933-50169d472540.png)

server {
        listen 80;
        listen [::]:80;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name build.uktechservice.in;

        location / {
                try_files $uri $uri/ =404;
        }
}

![image](https://user-images.githubusercontent.com/38104778/141679998-a0e1d8d1-25cb-4026-b0ec-eb4219614077.png)

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

Without domain name
server
     {
        listen 80 default_server;
        listen [::]:80 default_server;                                                                                  
        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;                                                             
        server_name _;                                                                                                  
       location / {
       proxy_pass http://172.31.8.33:3000;
       proxy_http_version 1.1;
       proxy_set_header Upgrade $http_upgrade;
       proxy_set_header Connection 'upgrade';
       proxy_set_header Host $host;
       proxy_cache_bypass $http_upgrade;
                    }                                                                                                   
    }

![image](https://user-images.githubusercontent.com/38104778/141680348-cd007e62-7642-4539-8674-07c54a557c12.png)
