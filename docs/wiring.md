# Wiring and GPIO Usage

## Assumptions
- The provided firmware is mapped to RP2040 GPIO numbers as shown in code.
- LEDs are active-high (GPIO HIGH turns LED on).
- LED cathodes are tied to GND in the Wokwi diagram.

## Keypad Connections
| Keypad Pin | Pico W GPIO | Purpose |
|---|---:|---|
| C1 | GP19 | Column scan input/output via Keypad lib |
| C2 | GP18 | Column scan input/output via Keypad lib |
| C3 | GP17 | Column scan input/output via Keypad lib |
| C4 | GP16 | Column scan input/output via Keypad lib |
| R1 | GP26 | Row scan input/output via Keypad lib |
| R2 | GP22 | Row scan input/output via Keypad lib |
| R3 | GP21 | Row scan input/output via Keypad lib |
| R4 | GP20 | Row scan input/output via Keypad lib |

Additionally, 1kΩ pull-up resistors in the diagram connect keypad rows to 3V3.

## LED Connections
### Blue LED Group (`1..8`)
| Logical LED | Trigger Key | Pico W GPIO |
|---|---|---:|
| LED1 | `1` | GP11 |
| LED2 | `2` | GP10 |
| LED3 | `3` | GP9 |
| LED4 | `4` | GP8 |
| LED5 | `5` | GP7 |
| LED6 | `6` | GP6 |
| LED7 | `7` | GP5 |
| LED8 | `8` | GP4 |

- `9`: turns ON all LEDs above.
- `0`: turns OFF all LEDs above.

### Red LED Group (`A..D`)
| Logical LED | Trigger Key | Pico W GPIO |
|---|---|---:|
| LED9 | `A` | GP3 |
| LED10 | `B` | GP2 |
| LED11 | `C` | GP28 |
| LED12 | `D` | GP27 |

- `*`: turns ON LED9..LED12.
- `#`: turns OFF LED9..LED12.

## Power and Ground
- Pico `3V3` is used for keypad row pull-up network.
- Pico `GND` is common ground for all LED cathodes.
- Each LED anode is driven from GPIO through a 220Ω resistor.
