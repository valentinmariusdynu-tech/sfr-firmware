# sfr-firmware

[![CI](https://github.com/valentinmariusdynu-tech/sfr-firmware/actions/workflows/ci.yml/badge.svg)](https://github.com/valentinmariusdynu-tech/sfr-firmware/actions/workflows/ci.yml)

ESP32 LoRa mesh firmware for the Signal For All Radio (SFR) device.

## Hardware
ESP32-WROOM · SX1276/SX1278 LoRa · PlatformIO · C++17

## Architecture
```
src/
├── main.cpp          — entry point and task scheduler
├── lora/             — LoRa transceiver driver (RadioLib)
├── mesh/             — mesh networking and packet routing
├── ble/              — Bluetooth pairing with sport-os-mobile
├── telemetry/        — sensor data encoding and transmission
└── config.h          — board pins and compile-time settings
test/
├── native/           — Unity unit tests (host, no hardware needed)
└── embedded/         — on-device integration tests
platformio.ini        — build environments
```

## Quick Start
```bash
# Install PlatformIO: https://platformio.org/install/cli
pio run --target upload   # build + flash to connected device
pio device monitor        # open serial monitor
```

## Dev Commands
```bash
pio run                   # build all environments
pio test -e native        # run host-side unit tests
pio run -e release        # release build (size-optimized)
pio check                 # static analysis (cppcheck)
```

## Related Repos
| Repo | Role |
|---|---|
| [sport-os-mobile](https://github.com/valentinmariusdynu-tech/sport-os-mobile) | BLE pairing counterpart |
| [sport-os-backend](https://github.com/valentinmariusdynu-tech/sport-os-backend) | Receives device telemetry |
| [sport-os-docs](https://github.com/valentinmariusdynu-tech/sport-os-docs) | Hardware documentation |
