All tips I summerized hereby are all based on my personal experience :)

1. setup zonetime if you use service like cron(run it in dockerfile is good idea)
```
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

2. deliver docker steps
```
#build image
docker build  --rm=true -t bartowski/autocheckin .
##run container and test function
docker run bartowski/autocheckin
##export image if test OK
docker save bartowski/autocheckin >  autocheckin.tar
#cp to server
scp -P 1989 autocheckin.tar admin@192.168.0.143:/volume1/docker/autocheckin.tar
```
3. If you want to compile it before push into the image, you can
```
## this cmd is useful if you use mac compile
CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo  github.com/chucklqsun/autocheckin
```

use scratch as your basic images, it's only 8M
Note: If you have anything issue or question, please leave me message in this repo
