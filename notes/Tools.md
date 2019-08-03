# Tools
首先是运行所需的工具的安装，按照教程的步骤是需要安装编译环境来编译QEMU

尝试在macOS上直接运行。

## 1. macOS运行

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

## 2. Ubuntu运行

到现在为止没出过什么问题，但是到了Lab1的时候就会发现，mac上要运行`gdb`非常麻烦，直接放弃，转向Linux虚拟机。

`Linux`发行版选择`Ubuntu 19.04`，最新的Ubuntu，并且选择了没有GUI的Server版（GUI没必要，还耗资源）。自带的命令行界面很难看，所以用外面终端ssh连到虚拟机上就好看了



由于Server版非常干净，几乎什么其他东西都没有，跟着教程一步步走就好，编译qemu几乎没有什么问题