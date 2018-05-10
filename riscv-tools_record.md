IT'S FAILT, but may be a good learning path.
-----------------------------------
# Environment

* [riscv-tools](https://github.com/riscv/riscv-tools)
* vim, vim vundle, YCM, YCM-Generator

## build RISC-V tools

1. git clone https://github.com/riscv/riscv-tools.git
2. cd riscv-tools
3. git submodule update --init --recursive
4. export RISCV=/path/to/install/riscv/toolchain    // I use /home/risc-v/.local/
5. ./build.sh
// You may need to login again.
6. cd ~
7. echo -e '#include <stdio.h>\n int main(void) { printf("Hello world!\\n"); return 0; }' > hello.c
8. spike pk hello
// Use full path, if 'could not open pk'
// That is bacuse they use absolute path, then you move the directory.(maybe)

## Linux/RISC-V installation

### Building riscv64-unknown-linux-gnu-gcc (11.41 SBU)

1. ./build-spike-only.sh
2. cd riscv-gnu-toolchain/
3. ./configure --prefix=$RISCV
4. make linux

### Building the Linux Kernel (0.40 + ε SBU)

5. cd ~
6. git clone https://github.com/riscv/riscv-linux.git linux-3.14.33
7. curl -L https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.14.33.tar.xz | tar -xJkf - // *
8. make ARCH=riscv defconfig                  // or 'menuconfig'
9. make ARCH=riscv -j[n] CROSS_COMPILE=riscv64-unknown-linux-gnu-
// if get error, use 'git checkout origin/master' to restore the state before 'curl'.

### Building BusyBox (0.26 SBU)

1. curl -L http://busybox.net/downloads/busybox-1.26.2.tar.bz2 > busybox-1.26.2.tar.bz2
2. tar xvjf busybox-1.26.2.tar.bz2
3. cd busybox-1.26.2
4. make allnoconfig
5. make -j[n]

# Reference

* [RISC-V 初探 | coldnew's blog](https://coldnew.github.io/c8717b7e/)

