# Kali-VM-for-Termux
These are cmds for getting a Kali VM in termux qemu
so first of all u need to make sure that all packages are up to date, u can do this by typing 
```bash
pkg update && pkg upgrade -y
```
now that all pkgs are up to date we can install QEMU utils (qemu means quick emulator)
```bash
pkg install qemu-utils qemu-x86_64-system aria2 -y
```
now we got qemu installed we need to make a virtual hard disk by typing
```bash
qemu-img create -f qcow2 kali.qcow2 80G
```
ok we have everything prepped now lets install the iso 
```bash
aria2c -x 16 -s 16 -k 1M "https://cdimage.kali.org/kali-2025.4/kali-linux-2025.4-installer-amd64.iso"
```
now we can make the params for the VM
```bash
qemu-system-x86_64 -m 2048 -cpu max -smp 2 -hda kali.qcow2 -cdrom kali-linux-2025.4-installer-amd64.iso -boot d -vga std -device e1000,netdev=net0 -netdev user,id=net0 -device ac97 -vnc :1
```
now connect to the VM with a vncviewer (server is 127.0.0.1 and port is 5901)
anyways yapped too much so cya! have fun! :)
(WARNING!!!!! THIS WILL BE KINDA SLOW WITHOUT KVM AND AFTER INSTALLKNG KALI ONLY RUN THE PARAMS AND CHANGE -BOOT D TO -BOOT C!!!!!!!!!!!!!!) (U NEED TO ALSO INSTALL AC97 DRIVERS OFF THE WEB!!!!!!!!!!!!!!!!)
