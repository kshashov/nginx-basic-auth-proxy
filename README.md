# nginx-basic-auth-proxy

## Example with [baget](https://github.com/loic-sharma/BaGet):
```yml
services:
  authenticate:
    image: "kshashov/nginx-basic-auth-proxy:latest"
    ports:
      - 80:80
    environment:
      - BASIC_AUTH_USERNAME=user
      - BASIC_AUTH_PASSWORD=pass
      - PROXY_PASS=http://baget/
      - CLIENT_MAX_BODY_SIZE=100m
      - SERVER_NAME=192.168.11.41
    restart: always
  baget:
    image: "loicsharma/baget"
    expose:
      - 80
    environment:
      - ApiKey=123
      - PackageDeletionBehavior=HardDelete
    restart: always
```
