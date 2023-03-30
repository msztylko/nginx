# nginx
Notes about nginx

### How to serve static content

The easiest way to do it, is to create alias to a file. Add `location` in the `server` section.

```nginx
location /docs {
    alias /path/to/my/docs/README.md;
}
```

### How to reload nginx configuration

1. Find PID of the master process

```bash
ps aux | grep -v grep | grep nginx                                                                                                                                                                       
nobody             309   0.0  0.0 409053920   1584   ??  S    27Feb23   0:00.01 nginx: worker process  
root               101   0.0  0.0 408660704     16   ??  Ss   27Feb23   0:00.02 nginx: master process /opt/homebrew/opt/nginx/bin/nginx -g daemon off; 
```

2. Soft kill
```bash
kill -HUP <nginx.pid>
```

### No port redirection

It is useful to add this option, so that redirects don't include port number in the URL.

```nginx
server {
    listen              8000;
    port_in_redirect    off;
    server_name         localhost;
```
