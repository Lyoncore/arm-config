# config for arm

## Prerequisites
- ubuntu-recovery-image: could be install from http://github.com/Lyoncore/ubuntu-recovery-image

## build recovery binary
``` bash
git clone https://github.com/Lyoncore/arm-config.git
cd arm-config/
go get launchpad.net/godeps
godeps -t -u dependencies.tsv

# For armhf (ex: pi3)
cd pi3
GOARCH=arm GOARM=7 CGO_ENABLED=1 CC=arm-linux-gnueabihf-gcc go run build.go build

# For arm64
GOARCH=arm64 CGO_ENABLED=1 CC=aarch64-linux-gnu-gcc go build -o local-includes/recovery/bin/recovery.bin ./src/
```

## generate image with ubuntu-recovery-image
``` bash
ubuntu-recovery-image
```

## run tests
``` bash
cd src
go test -check.vv
```
