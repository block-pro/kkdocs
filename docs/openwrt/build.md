# build

## step1

```bash
git clone https://github.com/coolsnowwolf/lede

#esir auto build
#git clone  https://github.com/esirplayground/AutoBuild-OpenWrt.git

#esir tut
#git clone https://github.com/esirplayground/Compile_OpenWrt_Tutorial.git
```

### 修改默认ip
```bash
sed -i 's/192.168.1.1/192.168.5.1/g' package/base-files/files/bin/config_generate
```

### 修改banner
```bash
vi package/base-files/files/etc/banner

KK OPENWRT, v1_2021.01.20, ENJOY IT
```

### 启用hello-world

```bash
sed -i 's/#src-git helloworld/src-git helloworld/g' ./feeds.conf.default
```

### ubuntu 20.04 env
```bash
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev patch unzip lib32gcc1 libc6-dev-i386 subversion flex gcc-multilib g++-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils libelf-dev autoconf automake libtool autopoint device-tree-compiler python2.7 zlib1g-dev upx-ucl node-uglify antlr3 gperf wget swig rsync

```

### feed

```bash
        ./scripts/feeds update -a
        ./scripts/feeds install -a
```

### 修改密码

```bash

```
### download

```bash
make download -j2
```

### Build 
```bash
make -j1 V=s
```
