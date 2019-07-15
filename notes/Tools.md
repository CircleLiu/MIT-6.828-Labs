# Tools
首先是运行所需的工具的安装，按照教程的步骤是需要安装编译环境来编译QEMU

一开始我是在Ubuntu虚拟机上安装Toolchain编译qemu，但是这样就是在虚拟机里运行模拟器，开销太大，因此我决定在macOS上直接运行，但是教程却没有详细说明如何在macOS下安装Toolchain，

直到我看到了这行
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