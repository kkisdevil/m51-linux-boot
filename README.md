# m51-linux-boot

Native Linux on the Samsung Galaxy M51 (SM-M515F, Snapdragon 730G / SM7150) — research-stage port.

## Status: research, no working boot yet

There is **no Linux port for m51 today** — no postmarketOS/Nura page, no Droidian / Ubuntu Touch port, no mainline device tree, no U-Boot entry. This repo is the work to change that, m51-first, not "universal Samsung".

## Why m51 could work

- The SM7150 SoC itself is well supported in mainline: the `sm7150-mainline` kernel and U-Boot cover 6 devices (Pixel 4a, Mi 9T/K20, Mi Note 10, Mi Note 10 Lite, POCO X3 NFC, Redmi Note 10 Pro) with a generic `qcom-sm7150` port.
- m51's sister device A71 is *almost* there: device-tree PRs are open and unmerged in `sm7150-mainline/linux` (#44) and `sm7150-mainline/u-boot` (#2).
- m51 foundation: unlockable bootloader (international model), TWRP 3.5.1, unofficial LineageOS 17.1/18.1/21.

## Two paths, in order

1. **Halium (Droidian / Ubuntu Touch)** — reusing the unofficial LineageOS 21 trees for m51 (`a71-devs`, kernel 4.14). The realistic first boot.
2. **Mainline postmarketOS (Nura)** — starting from the A71 device-tree work and adapting it to m51 (panel, touch, side fingerprint, 7000 mAh battery). The proper long-term path, weeks–months of kernel work. First boot would be display + USB + maybe Wi-Fi, not a daily driver.

## First milestone

Kernel booting to a shell over USB. Not a daily driver. Camera, modem/VoLTE, fingerprint and NFC are expected broken at first.

## What this is NOT

- Not Termux/proot — those are Linux userland inside Android, sharing Android's kernel. This is native boot.
- Not a universal Samsung Linux port — dual-boot and other devices come only after single-boot Linux works on m51.

## Dual boot

Dual-boot lives in the sister repo [m51-dualboot](https://github.com/kkisdevil/m51-dualboot) — it depends on this repo working first. There is no PC-style UEFI on a Samsung phone; the "UEFI" layer is U-Boot's EFI, chainloaded as a second stage.

## Licence and credits

GPL-3.0. See [CREDITS.md](CREDITS.md). Credit everyone whose repo, tool, guide or info is used.
