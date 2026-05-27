# libreboot-nidhoggr

personal libreboot patches for thinkpad t480, based on libreboot 26.01.

## changes

- `CONFIG_MAINBOARD_SMBIOS_PRODUCT_NAME="ThinkPad T480"` — required for tlp 1.8+ battery thresholds via natacpi
- `CONFIG_FSP_HYPERTHREADING=y` — smt enabled, 8 threads on i5/i7-8xxx
- `CONFIG_H8_FN_CTRL_SWAP=y` — fn/ctrl swap at ec level
- `f1_to_f12_as_primary` default → 0 — hotkeys primary on boot (fnlock off); cmos doesn't persist this on t480 with libreboot
- `payload_grubsea` — grub primary, seabios accessible from grub menu
- `set timeout=0` — no grub delay

## apply

```sh
cd lbmk  # at tag 26.01
cp ../0052-ec-h8-default-f1_to_f12_as_primary-to-0-hotkeys-primary.patch config/coreboot/default/patches/
git apply ../0001-t480-personal-customizations.patch
```

## build (nixos)

```sh
nix-shell  # drop shell.nix in lbmk root first
./build roms targets/t480_vfsp_16mb
```

shell.nix adapted from https://catstret.ch/202505/libreboot-build-nix/
