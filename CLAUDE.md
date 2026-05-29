# sfr-firmware — Stack Conventions

## Hardware Target
- MCU: ESP32 (Arduino framework via PlatformIO)
- Radio: SX1276/SX1278 LoRa module
- Build system: PlatformIO

## Stack
- Language: C / C++17
- LoRa library: RadioLib (preferred)
- Mesh: Signal For All Radio custom protocol

## Code Conventions
- PlatformIO layout: src/, include/, lib/, test/
- Naming: snake_case for C; CamelCase for C++ classes
- All pin assignments in include/board_config.h
- No dynamic allocation inside ISRs

## Testing
- Unity framework via pio test -e native
- Hardware-in-loop tests documented in test/README.md

## Git
- Conventional commits (feat:, fix:, hw:)
- Binary artifacts (.bin, .elf, .map) excluded
- Release tags trigger firmware build and GitHub Release assets
