# On Linux(Debian/Ubuntu) Install qemu and nasm

`sudo apt-get install qemu`

`sudo apt-get install nasm`

To Compile:

`nasm -f bin some-file.asm -o some-file.bin`

To run execute

`qemu-system-x86_64 some-file.bin`
