docker build -t fpm .
docker run --rm -it -v $PWD/conf/:/usr/local/etc/ fpm bash

