# POCimage for board chart on aws

how to get images form nginx：

add it to nginx.conf

``` php
location ~ .*\.(gif|jpg|jpeg|png)$ {  
  expires 24h;  
    root /home/images/;#指定图片存放路径  
    access_log /usr/local/websrv/nginx-1.9.4/logs/images.log;#日志存放路径  
    proxy_store on;  
    proxy_store_access user:rw group:rw all:rw;  
    proxy_temp_path     /home/images/;#图片访问路径  
    proxy_redirect     off;  
    proxy_set_header    Host 127.0.0.1;  
    client_max_body_size  10m;  
    client_body_buffer_size 1280k;  
    proxy_connect_timeout  900;  
    proxy_send_timeout   900;  
    proxy_read_timeout   900;  
    proxy_buffer_size    40k;  
    proxy_buffers      40 320k;  
    proxy_busy_buffers_size 640k;  
    proxy_temp_file_write_size 640k;  
    if ( !-e $request_filename)  
    {  
       proxy_pass http://127.0.0.1;#默认80端口  
    }  
}
```
