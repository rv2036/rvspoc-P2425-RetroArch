Team name: me0wall

## Environment Setup

As I only learned about the competition the day before it ended, I didn't have time to wait for the development machine authorization, so I completed all the work in qemu.

The OS is Debian trixie/sid, with a kernel version of 6.9.12-riscv64.

qemu version is 9.0.50 and the host environment is Windows x86_64.

Install dependencies:

```shell
apt-get -y install build-essential libxkbcommon-dev zlib1g-dev libfreetype6-dev libegl1-mesa-dev libgles2-mesa-dev libgbm-dev nvidia-cg-toolkit nvidia-cg-dev libavcodec-dev libsdl2-dev libsdl-image1.2-dev libxml2-dev yasm libcurl4-openssl-dev libpcap-dev libx11-xcb-dev
```

## Build

### RetroArch

No modifications needed, just compile directly.

```shell
git clone https://github.com/CatMe0w/rvspoc-P2425-RetroArch
cd rvspoc-P2425-RetroArch
./configure
make clean
make
```

### ppsspp

No modifications needed, just compile directly.

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh ppsspp
./libretro-build.sh ppsspp
```

### flycast

I have completed the initial adaptation for riscv32 and riscv64, and it can be compiled and run.

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh flycast
./libretro-build.sh flycast
```

Precompiled binaries have been uploaded to https://github.com/CatMe0w/rvspoc-P2425-RetroArch/releases

## Additional Targets

### flycast without RetroArch dependency

During the adaptation of flycast, I also completed the adaptation of standalone flycast, which can be compiled and run.

```shell
git clone https://github.com/CatMe0w/flycast
cd flycast
mkdir build
cd build
cmake ..
make
```

### Other RetroArch Cores

These cores can be compiled directly. Since qemu is slow, the cores listed here may continue to be added before the competition ends.

```shell
git clone https://github.com/CatMe0w/libretro-super
cd libretro-super
./libretro-fetch.sh nestopia snes9x mgba
./libretro-build.sh nestopia snes9x mgba
```
