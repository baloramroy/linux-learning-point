## `/boot` – Bootloader files

```
/boot/
├── vmlinuz-6.1.0-amd64          # Linux kernel
├── initramfs-6.1.0-amd64.img    # Initial RAM filesystem
├── grub/                        # GRUB bootloader
│   ├── grub.cfg                 # Boot menu configuration
│   └── fonts/                   # Boot menu fonts
└── efi/                         # EFI partition (UEFI systems)
    └── EFI/ubuntu/grubx64.efi   # UEFI bootloader
```
