# Firmware Architecture

## Scope
This project intentionally preserves the original control behavior and key-to-LED mapping.

## Source Layout
- `src/main.cpp`
  - Global constants:
    - `LEDS = 12`, `ROWS = 4`, `COLS = 4`
  - Static key map matrix (`keys[4][4]`)
  - Pin mapping arrays:
    - `ledPins[12]`
    - `rowPins[4]`
    - `colPins[4]`
  - `Keypad` object initialization
  - `setup()`:
    - Configures all LED GPIOs as outputs and initializes LOW
  - `loop()`:
    - Polls keypad (`keypad.getKey()`)
    - Executes switch-case command routing
    - Debounce/poll pacing via `delay(10)`

## Behavioral Model
1. System boots and clears all 12 LED outputs.
2. Main loop polls one key event at a time.
3. If a key is detected:
   - Single key commands set one LED HIGH.
   - Group commands iterate through LED ranges and set HIGH/LOW.
4. No state machine memory beyond GPIO output latches.

## Non-Functional Notes
- No Wi-Fi stack use.
- No serial logging required by logic.
- Polling-based input handling with fixed 10ms loop delay.
