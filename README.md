# ESP8266 RTOS Project Boilerplate

## Requirements

- [Make utility](https://manpages.ubuntu.com/manpages/cosmic/man1/make.1.html)
- [ESPRESSIF ESP Toolchain for Linux](https://github.com/va1da5/esp-toolchain-docker)

## Get Started

Clone the boilerplate repository

```bash
git clone https://github.com/va1da5/esp8266-rtos-boilerplate.git my-awesome-project
```

The boilerplate contains a `bootstrap.sh` utility script which initiates missing project pieces. Execute the following to get started.

```bash
./bootstrap.sh
Enter project name: my-awesome-project
```

The utility script will provision `Makefile` which will point to ESP8266 RTOS SDK. It is not required to have SDK installed in the host machine. It can be used from a dedicated [container image](https://github.com/va1da5/esp-toolchain-docker). The container image needs to be build before moving further.

Once container images with `esp8266` development tools are ready, we can start it and begin our development journey. Please update the device definition (`--device=/dev/ttyUSB0`) in the docker run command based on your setup.

```
current_dir=${PWD##*/}; docker run --rm -it -v "${PWD}:/${current_dir}" -w "/${current_dir}" --device=/dev/ttyUSB0  esp8266

# configures project settings (serial device, flash size)
root@e7c862f46b0c:/my-awesome-project# make menuconfig

# builds project binaries, loads into esp8266 and monitors serial output
root@e7c862f46b0c:/my-awesome-project# make all flash monitor
```

## References

- [ESP8266 RTOS Software Development Kit](https://github.com/espressif/ESP8266_RTOS_SDK)
- [FreeRTOS Documentation](https://www.freertos.org/Documentation/RTOS_book.html)
- [ESP8266 Modules Reference](https://www.esp8266.com/wiki/doku.php?id=esp8266-module-family)
