# libreboot-nidhoggr

personal libreboot patches for thinkpad t480, based on libreboot 26.01.

## changes

- `CONFIG_FSP_HYPERTHREADING=y` — smt enabled, 8 threads on i5/i7-8xxx
- `CONFIG_H8_FN_CTRL_SWAP=y` — fn/ctrl swap at ec level
- `payload_grubsea` — grub primary, seabios accessible from grub menu
- `set timeout=0` — no grub delay

## apply

```sh
cd lbmk  # at tag 26.01
git apply 0001-t480-personal-customizations.patch
```

## build (nixos)

```sh
nix-shell  # drop shell.nix in lbmk root first
./build roms targets/t480_vfsp_16mb
```

shell.nix adapted from https://catstret.ch/202505/libreboot-build-nix/
