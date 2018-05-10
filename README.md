# Now use freedom-u-sdk

1. git clone https://github.com/sifive/freedom-u-sdk.git
2. cd freedom-u-sdk
3. git submodule update --init --recursive
4. unset RISCV
5. sudo make

For glibc-2.27 up, see https://github.com/sifive/freedom-u-sdk/issues/52 

Need 'libg.lib2.0-dev' for qemu

# Reference

[HiFive Unleashed Getting Started Guide | SiFive](https://www.sifive.com/documentation/boards/hifive-unleashed/hifive-unleashed-getting-started-guide/)

