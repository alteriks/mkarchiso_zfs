# Arch Linux Archiso builder with zfs support
## Prerequisite
```bash
pacman -syu archiso
yay -syu ventoy-bin
```
## Prepare ISO
```bash
sudo mkarchiso -v -w /home/alteriks/tmp/arch/dynamic_data -o out arch_template
```
## Ventoy workaround
It seems that Ventoy in UEFI mode uses hardcoded 'linux-vmlinuz' entry in it's hooks, so zfs-linux hangs during boot with:
"Waiting 30 seconds for device /dev/disk/by-label/ARCHLINUX..."
File arch_template/airootfs/etc/pacman.d/hooks/linux-dummy.hook contains workaround. It renames vmlinuz-linux-lts to vmlinuz-linux
