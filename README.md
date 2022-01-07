# Stack
[![static analysis](https://github.com/z-ev/course.stack/actions/workflows/static-analysis.yml/badge.svg?branch=dev&event=push)](https://github.com/z-ev/course.stack/actions/workflows/static-analysis.yml)
[![create package](https://github.com/z-ev/course.stack/actions/workflows/release-package.yml/badge.svg?event=release)](https://github.com/z-ev/course.stack/actions/workflows/release-package.yml)
## Docker 
```
$ cd ./docker
$ cp ./.env.docker ./.env
$ echo "127.0.0.1 stack.loc" | sudo tee -a /etc/hosts
$ docker-compose uo -d --build
$ xdg-open http://stack.loc:8089
```
