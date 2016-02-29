# HTTP Request Timeout

- xmlhttprequest.abort => status code 0

# Nginx Limitation

- client_max_body_size: 1M
- fastcgi_read_timeout: 60s

Defines a timeout for reading a response from the FastCGI server. The timeout is set only between two successive read operations, not for the transmission of the whole response. If the FastCGI server does not transmit anything within this time, the connection is closed.

# PHP Limitation

- memory_limit: 128M
- post_max_size: 8M
- upload_max_filesize: 2M
- max_execution_time: 30s

    CLI is unlimited

    Both set_time_limit(...) and ini_set('max_execution_time',...) won't count the time cost of sleep, file_get_contents, shell_exec, mysql_query etc
