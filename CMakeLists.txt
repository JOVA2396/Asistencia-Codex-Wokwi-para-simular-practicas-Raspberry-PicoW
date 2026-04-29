cmake_minimum_required(VERSION 3.13)

project(pico_w_keypad_leds C CXX)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# NOTE:
# The firmware source uses Arduino APIs and the Keypad library.
# Build this project using an Arduino-compatible RP2040 core (e.g., Arduino IDE/CLI or Wokwi),
# or adapt the implementation to Pico SDK APIs if native Pico SDK build is required.

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use src/main.cpp with Arduino RP2040 core (Wokwi-compatible)."
)
