# Tools
首先是运行所需的工具的安装，按照教程的步骤是需要安装编译环境来编译QEMU

一开始我是在Ubuntu虚拟机上安装Toolchain编译qemu，但是这样就是在虚拟机里运行模拟器，开销太大，因此我决定在macOS上直接运行。

## Homebrew直接安装

教程中有这么一行
```bash
brew install $(brew deps qemu)
```
安装qemu所需的依赖包

那说明`homebrew`里就有qemu，不需要我自己编译

所以直接
```bash
brew install qemu
```

然后安装完成

## 自己编译qemu

据说教程提供的qemu是修改过的，不使用教程提供的可能会有某些调试信息无法显示，遂决定自己重新编译qemu

### 1. 安装依赖

安装qemu所需的依赖

```bash
brew install $(brew deps qemu)
```

根据https://github.com/lizebang/jos-xv6-macOS
需要安装`make`所需的两个依赖包

```bash
brew tap liudangyi/i386-jos-elf-gcc
brew install i386-jos-elf-gcc i386-jos-elf-gdb
```

再安装`pkg-config`

```bash
brew install pkg-config
```

### 2. Python2环境

这玩意在配置时候需要用到`Python2`

在Anaconda创建一个新的环境

```bash
conda create -n py2 python=2.7
```

创建好以后编译之前要进到这个环境里面

```bash
conda activate py2
```

### 3. 编译

先克隆仓库

```bash
git clone https://github.com/mit-pdos/6.828-qemu.git qemu
```

配置

```bash
./configure --disable-kvm --disable-werror --disable-sdl --target-list="i386-softmmu x86_64-softmmu"
```

编译并安装

```bash
make && make install
```

没报错，就OK了