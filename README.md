# Getting started with the Nordic nRF52840 board in rust.

## Linux Instalation instructions.

Install Rust (rustc, cargo, rustup)

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Install `probe-run`

```
cargo install probe-run
```
If it fails on wsl, use 
```
sudo apt install build-essential
sudo apt install libudev-dev
sudo apt install pkg-config
```
```
rustup target add thumbv7em-none-eabihf
```

Add UDEV rules (to a new file in `/etc/udev/rules.d/`)
```
ATTRS{idVendor}=="1366", ENV{ID_MM_DEVICE_IGNORE}="1", TAG+="uaccess"
```
you can do it by:

```
sudo touch /etc/udev/rules.d/nrf
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="1366", ATTR{idProduct}=="1015", MODE="0666", TAG+="uaccess"' | sudo tee /etc/udev/rules.d/nrf

sudo usermod -aG plugdev $USER
newgrp plugdev

sudo udevadm control --reload-rules
sudo udevadm trigger
```

Plug in the board and switch it on.

```
cargo run
```

## Getting the boards

I've been using the NRF52840-DK board (about 40-50 euros)

https://www.digikey.co.uk/en/products/detail/nordic-semiconductor-asa/NRF52840-DK/8593726

But there is a cheaper version here (about 10 euros)

https://www.digikey.co.uk/en/products/detail/nordic-semiconductor-asa/NRF52840-DONGLE/9491124

Other vendors are available!

## Course outline

[Course Outline](COURSE-OUTLINE.md)

## Exercises

[Exercises](EXERCISES.md)

## Documentation essential reading.

[Documentation](DOCUMENTATION.md)
