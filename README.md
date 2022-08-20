# openwrt-docker

### 构建镜像
```bash
$ git clone git@github.com:garryshield/openwrt-docker.git
$ cd openwrt-docker
$ docker build -t openwrt-docker ./
```

### 下载源码
```bash
$ cd openwrt-docker
$ git clone git@github.com:coolsnowwolf/lede.git
$ docker run -it --rm -v $(pwd)/lede:/home/ubuntu/lede openwrt-docker /bin/bash
```

### 更新 feeds 
```bash
$ id
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)
$ pwd
/home/ubuntu

$ cd ~/lede
$ ./scripts/feeds clean
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
$ ./scripts/feeds install -a
```

注：第一次执行 `./scripts/feeds install -a` 可能会出现 `WARNING` 再执行一次就不会出现
原因见：[issues/4731](https://github.com/coolsnowwolf/lede/issues/4731)

### 选择配置
```bash
# 生成默认配置 .config
$ make defconfig
```

```bash
# 手动修改配置 .config
$ make menuconfig
```

### 编译固件
```bash
$ make download -j$(nproc)
$ make V=s -j1
```

### 二次编译
```bash
$ id
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)
$ pwd
/home/ubuntu

$ cd ~/lede
$ git pull
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
$ make defconfig
$ make download -j$(nproc)
$ make V=s -j$(nproc)
```

#### 重新配置
```bash
$ rm -rf ./tmp && rm -rf .config*
$ make menuconfig
$ make download -j$(nproc)
$ make V=s -j$(nproc)
```

参考链接：
- [Lean's OpenWrt source](https://github.com/coolsnowwolf/lede)
