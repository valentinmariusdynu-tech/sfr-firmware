# CLAUDE.md — sfr-firmware

## Purpose
ESP32 C++17 firmware for the SFR (Signal For All Radio) device. Implements LoRa mesh networking, BLE pairing with sport-os-mobile, and telemetry transmission to sport-os-backend.

## Stack
- C++17, PlatformIO
- ESP32 (Arduino framework over ESP-IDF)
- RadioLib (LoRa SX1276/SX1278)
- Unity (unit tests via PlatformIO native env)
- cppcheck (static analysis)

## Key Directories
- `src/lora/` — LoRa PHY driver wrapping RadioLib
- `src/mesh/` — mesh routing and packet forwarding
- `src/ble/` — Bluetooth pairing protocol
- `src/telemetry/` — sensor data packing (binary protocol)
- `src/config.h` — pin definitions and compile-time knobs
- `test/native/` — Unity tests runnable without hardware (`pio test -e native`)

## Dev Commands
```bash
pio run                    # build
pio run --target upload    # build + flash
pio test -e native         # unit tests (host)
pio check                  # cppcheck static analysis
pio device monitor         # serial console
```

## Conventions
- All hardware pin numbers defined in `config.h`; never hardcode in `.cpp`
- Binary telemetry packets use little-endian byte order
- Keep ISR handlers minimal; defer work to FreeRTOS task queues
- Test with native env first; flash only for hardware integration tests

## Related Repos
- [sport-os-mobile](https://github.com/valentinmariusdynu-tech/sport-os-mobile) — BLE counterpart
- [sport-os-backend](https://github.com/valentinmariusdynu-tech/sport-os-backend) — telemetry receiver
