# Live VM

## Create data disk
```shell
~ % qemu-img create -f qcow2 data_disk.qcow2 100M
```

## Launch Live VM
```shell
~ % qemu-system-x86_64 -m 8G -smp 4 -cdrom Downloads/Fedora-Workstation-Live-x86_64-40-1.14.iso -drive file=data_disk.qcow2,if=virtio -vga virtio -display default,show-cursor=on -usb -device usb-tablet -cpu host -machine type=q35,accel=hvf
```
