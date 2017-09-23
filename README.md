Filebeat for nginx
------------------

How to use?
===========

### Run Filebeat

In nginx logs directory

```bash
docker run --rm -v `echo $( pwd )`:/var/log/nginx/ -e LOGSTASH_HOST='172.17.0.1' mishamx/filebeat-nginx:latest
```

or set full path

```bash
docker run --rm -v /var/log/nginx:/var/log/nginx/ -e LOGSTASH_HOST='172.17.0.1' mishamx/filebeat-nginx:latest
```

Environment
===========
| ENV           | Default  |
|---------------|----------|
|`LOGSTASH_HOST`| logstash |
|`LOGSTASH_PORT`|   5044   |
|`INDEX_NAME`   |   nginx  |
|`ENCODING`     |   utf-8  |

Docker Compose
==============

```
version: '3.3'

services:

    filebeat_nginx:
        image: filebeat-nginx:latest
        volumes:
          - /var/log/nginx:/var/log/nginx/
        environment:
          LOGSTASH_HOST: "172.17.0.1"
          LOGSTASH_PORT: "5044"
          INDEX_NAME: "nginx"
          ENCODING: "utf-8"
```
