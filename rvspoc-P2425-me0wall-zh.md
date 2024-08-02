队伍名：me0wall

## 环境配置

由于本人在结束前一天才了解到比赛，已经来不及等待开发机授权，因此在 qemu 中完成了所有的工作。

所使用的系统为 Debian trixie/sid，内核版本为 6.9.12-riscv64。

qemu 版本为 9.0.50，宿主环境为 Windows x86_64。

安装依赖：

```shell
apt-get -y install build-essential libxkbcommon-dev zlib1g-dev libfreetype6-dev libegl1-mesa-dev libgles2-mesa-dev libgbm-dev nvidia-cg-toolkit nvidia-cg-dev libavcodec-dev libsdl2-dev libsdl-image1.2-dev libxml2-dev yasm libcurl4-openssl-dev libpcap-dev libx11-xcb-dev
```

## 编译

### RetroArch

无需改动，直接编译即可。

```shell
git clone https://github.com/CatMe0w/rvspoc-P2425-RetroArch
cd rvspoc-P2425-RetroArch
./configure
make clean
make
```

### ppsspp

无需改动，直接编译即可。

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh ppsspp
./libretro-build.sh ppsspp
```

### flycast

我完成了初步的 riscv32 与 riscv64 适配，已经能够通过编译和运行。

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh flycast
./libretro-build.sh flycast
```

预编译的二进制文件已经上传至 https://github.com/CatMe0w/rvspoc-P2425-RetroArch/releases。

## 额外目标

### 不依赖 RetroArch 的 flycast

在适配 flycast 时，也一并完成了独立 flycast 的适配，已经能够通过编译和运行。

```shell
git clone https://github.com/CatMe0w/flycast
cd flycast
mkdir build
cd build
cmake ..
make
```

### 其他 RetroArch 核心

这些核心可以直接编译。由于 qemu 很慢，此处列出的核心可能在比赛结束前持续追加。

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh nestopia snes9x mgba
./libretro-build.sh nestopia snes9x mgba
```
