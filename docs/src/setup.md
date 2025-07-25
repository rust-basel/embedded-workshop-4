# Setup

This chapter will cover the setup of the workshop environment. We will start by installing the necessary tools and setting up the development environment. [source](https://docs.espressif.com/projects/rust/book/installation/riscv.html)

## Development Environment

This downloads the rust source code. This is needed to build custom targets targeting a triple-target that is not yet supported by rust.

```sh
rustup toolchain install stable --component rust-src
```

The toolchain for the ESP32-C3

```sh
rustup target add riscv32imc-unknown-none-elf
```

- riscv32imc:
  - riscv32: 32-bit RISC-V instruction set architecture
  - i: Base integer instruction set
  - m: Base integer instruction set with multiplication and division
  - c: Base integer instruction set with compressed instructions
- unknown: Vendor field - no specific vendor is targeted
- none: operation system (bare-metal)
- elf: Executable and linkable binary format (calling convenction)

### Probe-RS

This is the recommended tool for flashing and and interacting (e.g. debugging) with the ESP32-C3.

NOTE: Package installation for different Linux distributions:

**udev rules:**

Follow: https://probe.rs/docs/getting-started/probe-setup/#linux%3A-udev-rules


**Debian/Ubuntu:**
```sh
sudo apt install -y pkg-config libudev-dev cmake git
```

**Fedora:**
```sh
sudo dnf install -y pkgconfig systemd-devel cmake git
```


```sh
cargo install probe-rs-tools
```

## Tools to build a project

To generate a project you need esp-generate.

```sh
cargo install esp-generate
```

To then generate a project run the following command: (TODO: Check, which [options](https://github.com/esp-rs/esp-generate?tab=readme-ov-file#available-options) are needed)

```sh
esp-generate --chip esp32c3 --headless -o probe-rs -o defmt hello_world
```

You can see all the other options you can use to generate a project [here](https://github.com/esp-rs/esp-generate?tab=readme-ov-file#available-options)

## Flashing

```sh
cargo run --release
```
