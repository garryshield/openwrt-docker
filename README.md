# openwrt-docker

```bash
$ git clone git@github.com:garryshield/openwrt-docker.git
$ cd openwrt-docker
$ docker build -t openwrt-docker ./
```

```bash
$ cd openwrt-docker
$ git clone git@github.com:coolsnowwolf/lede.git
$ docker run -it --rm -v $(pwd)/lede:/home/ubuntu/lede openwrt-docker /bin/bash
```

```bash
$ id
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)

$ cd ~/lede
$ ./scripts/feeds clean
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
$ ./scripts/feeds install -a
```

注：第一次执行 `./scripts/feeds install -a` 可能会出现 `WARNING` 再执行一次就不会出现
原因见：[](https://github.com/coolsnowwolf/lede/issues/4731)

```bash
$ make menuconfig
```