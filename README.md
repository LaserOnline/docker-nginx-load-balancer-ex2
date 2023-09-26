
![Logo](https://github.com/LaserOnline/docker-nginx-load-balancer-ex1/assets/51033703/7b87b976-4819-4997-b564-d2a78818804b)


## Nginx

Nginx.conf

```bash
  upstream nestjs {
    server api-nestjs-1:3000 weight=6;
    server api-nestjs-2:3000 weight=4;
}

server {
    listen 80;
    server_tokens off;

    location / {
        proxy_pass http://nestjs;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_intercept_errors on;
    }
}
```

