# Rampon Anchor Firmware

## Loading Release Builds

- TODO

After flashing completes, the device should be available as:
`/dev/serial/by-id/usb-Anchor_rampon_anchor_static-if00`.

## Klipper Config

```ini
[mcu rampon]
serial: /dev/serial/by-id/usb-Anchor_rampon_anchor_static-if00

[adxl345]
cs_pin: rampon:CS

[resonance_tester]
accel_chip: adxl345
probe_points: 90, 90, 20
```

## Developers

---

## Building Firmware

To compile the project, you will need a Rust toolchain installed, `cargo-binutils`, and the compile target for ARM Cortex-M0. They can be installed with:

```
% rustup component add llvm-tools-preview
% rustup target add thumbv6m-none-eabi
```

To build the project run:

```
% cargo build --release --target thumbv6m-none-eabi
```

To flash an RP2040 connected over USB in bootloader mode, run:

```
% sudo elf2uf2-rs -d target/thumbv6m-none-eabi/release/rampon_anchor
```

After the update completes, the device should be available as:
`/dev/serial/by-id/usb-Anchor_rampon_anchor_static-if00`.
