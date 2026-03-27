## import image
```shell
wget -O /tmp/wallence.tar --no-proxy
podman load -i /tmp/wallence.tar
```

## provide config in .env

## start proxy service
```shell
podman-compose up -d --rm
```
## set env
```shell
local MIXED_PORT=7890  # the same to docker-compose.yaml
local http_proxy_addr="http://127.0.0.1:${MIXED_PORT}"
local socks_proxy_addr="socks5h://127.0.0.1:${MIXED_PORT}"
local no_proxy_addr="localhost,127.0.0.1,::1"

export http_proxy=$http_proxy_addr
export https_proxy=$http_proxy
export HTTP_PROXY=$http_proxy
export HTTPS_PROXY=$http_proxy

export all_proxy=$socks_proxy_addr
export ALL_PROXY=$all_proxy

export no_proxy=$no_proxy_addr
export NO_PROXY=$no_proxy
```
## clean up
clean container
```shell
podman-compose down
```

clean proxy env
```shell
unset http_proxy
unset https_proxy
unset HTTP_PROXY
unset HTTPS_PROXY
unset all_proxy
unset ALL_PROXY
unset no_proxy
unset NO_PROXY
```
