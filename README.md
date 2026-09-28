# HUT OS — Linux configuration

Kernel configuration and build notes for **HUT OS**.

This repository does **not** contain the Linux kernel source. HUT OS builds against [upstream Linux](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git).

## Contents

- `hutos_defconfig` — kernel configuration used by HUT OS
- `README.md` — build instructions

## Build

```bash
git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
git checkout v7.3-rc5   # or a tested newer tag

curl -fsSL \
  https://raw.githubusercontent.com/hut-os/linux-config/main/hutos_defconfig \
  -o .config

make olddefconfig
make -j"$(nproc)" bzImage
```

Place `arch/x86/boot/bzImage` where the [hut-os](https://github.com/hut-os/hut-os) build expects it:

```text
hut-os/kernel/arch/x86/boot/bzImage
```

## Branding

`CONFIG_LOCALVERSION="-HUTOS-Hamedan-University-of-Technology"`

## License

Configuration files follow Linux kernel licensing (GPL-2.0).
