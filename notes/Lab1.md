#Lab 1: Booting a PC

## 运行起来

1. 首先先把仓库拉下来

   ```bash
   git clone https://pdos.csail.mit.edu/6.828/2018/jos.git lab
   ```

2. 然后编译

   ```bash
   cd lab
   make
   ```

## Part 1: PC Bootstrap

### Simulating the x86
使用下面命令运行，就不会弹出一个单独的命令行界面，也不会隐藏鼠标，而是直接在本地Terminal中显示
```bash
make qemu-nox
```

