# Raspberry Pi Pico W - 4x4 Keypad to 12 LEDs Controller

## Project Overview
This repository contains a Raspberry Pi Pico W firmware project that reads a 4x4 membrane keypad and controls 12 LEDs based on key presses. The behavior is preserved exactly from the provided source logic.

- Keys `1..8` turn on individual blue LEDs.
- Key `9` turns on all blue LEDs (`1..8`).
- Key `0` turns off all blue LEDs (`1..8`).
- Keys `A..D` turn on individual red LEDs.
- Key `*` turns on all red LEDs (`A..D`).
- Key `#` turns off all red LEDs (`A..D`).

## Repository Structure
- `src/main.cpp`: Main firmware logic (unchanged behavior).
- `include/`: Reserved for headers when splitting modules in the future.
- `diagram.json`: Wokwi hardware diagram.
- `docs/wiring.md`: Hardware wiring and GPIO map.
- `docs/architecture.md`: Code architecture and runtime behavior.
- `CMakeLists.txt`: Project metadata and build note for Arduino-style source.

## Components List (from diagram)
- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220Ω resistors (one per LED)
- 4x 1kΩ resistors (keypad row pull-ups)
- Jumper wires

## GPIO Mapping Summary
| Function | Pico GPIO |
|---|---|
| LED 1..8 outputs | GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4 |
| LED A..D outputs | GP3, GP2, GP28, GP27 |
| Keypad rows R1..R4 | GP26, GP22, GP21, GP20 |
| Keypad columns C1..C4 | GP19, GP18, GP17, GP16 |

> Full mapping and keypad/LED cross-reference are in `docs/wiring.md`.

## Run in Wokwi
1. Create/import this project in Wokwi.
2. Ensure `src/main.cpp` is used as the sketch source.
3. Use `diagram.json` for the circuit.
4. Start simulation and press keypad buttons.

## Run on Real Hardware (Pico W)
### Option A: Arduino IDE (recommended for this source)
1. Install Arduino IDE 2.x.
2. Install an RP2040-compatible board package (e.g., Arduino-Pico by Earle Philhower).
3. Install the `Keypad` library from Library Manager.
4. Select board: **Raspberry Pi Pico W**.
5. Copy `src/main.cpp` into your sketch (or rename to `.ino` in Arduino workflow).
6. Wire according to `docs/wiring.md`.
7. Build and upload.

### Option B: Arduino CLI
1. Install `arduino-cli`.
2. Install RP2040 core and `Keypad` library.
3. Compile/upload targeting Pico W.

## Wi-Fi Notes
This firmware does not use Wi-Fi, despite running on Pico W hardware.
No credentials are required and none are stored in this repository.
