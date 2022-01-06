# Stack

## Docker 
```
$ cd ./docker
$ cp ./.env.docker ./.env
$ echo "127.0.0.1 stack.loc" | sudo tee -a /etc/hosts
$ docker-compose uo -d --build
$ xdg-open http://stack.loc:8089
```
