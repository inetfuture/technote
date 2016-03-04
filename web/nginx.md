# Proxy With CORS

```nginx
server {
  listen 80;

  location / {
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    # Nginx doesn't support nested If statements, so we
    # concatenate compound conditions on the $cors variable and process later

    # If request comes from allowed subdomain then we enable CORS
    if ($http_origin ~* (http?://.*(:[0-9]+)?$)) {
       set $cors "1";
    }

    # OPTIONS indicates a CORS pre-flight request
    if ($request_method = 'OPTIONS') {
       set $cors "${cors}o";
    }

    # Append CORS headers to any request from allowed CORS domain, except OPTIONS
    # always parameter requires Nginx 1.7.5+
    if ($cors = "1") {
       add_header Access-Control-Allow-Origin $http_origin always;
       add_header Access-Control-Allow-Credentials true always;
    }

    # OPTIONS (pre-flight) request from allowed CORS domain. return response directly
    if ($cors = "1o") {
       add_header Access-Control-Allow-Origin $http_origin;
       add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS, PUT, DELETE';
       add_header Access-Control-Allow-Credentials true;
       add_header Access-Control-Allow-Headers 'Origin,Content-Type,Accept';
       add_header Content-Length 0;
       add_header Content-Type text/plain;
       return 204;
    }

    proxy_pass http://domain:port;
  }
}
```
