### Fast reboot

Does not cycle power on HDDs. Allows for faster experimentation when messing with systemd services.

(For the LTS kernel)
```
# kexec -l /boot/vmlinuz-linux-lts --initrd=/boot/initramfs-linux-lts.img --reuse-cmdline
# systemctl kexec
```

See [the Arch wiki](https://wiki.archlinux.org/title/Kexec)
