# Live VM

## Create data disk
```shell
~ % qemu-img create -f qcow2 data_disk.qcow2 100M
```

## Launch x86 Live VM

## On Intel Mac with native CPU host
```shell
~ % qemu-system-x86_64 -m 8G -smp 4 -cdrom Downloads/Fedora-Workstation-Live-x86_64-40-1.14.iso -drive file=data_disk.qcow2,if=virtio -vga virtio -display default,show-cursor=on -usb -device usb-tablet -cpu host -machine type=q35,accel=hvf
```

## On Apple Silicon with emulation layer
```shell
~ % qemu-system-x86_64 -m 8G -smp 4 -cdrom Downloads/Fedora-Workstation-Live-x86_64-40-1.14.iso -drive file=data_disk.qcow2,if=virtio -vga virtio -display default,show-cursor=on -usb -device usb-tablet
```

## Format Data Disk
Once in the booted Live VM, inside a terminal:
```shell
lsblk
```
If you booted the Live VM with just one attached virtual disk, you should see a `/dev/vda`:
```shell
su
mkfs.ext4 /dev/vda
mkdir /mnt/data
mount /dev/vda /mnt/data
```
