# Microcontroller Timers and Interrupts

Bare-metal C firmware for a Microchip PIC24 microcontroller (MPLAB X, XC16 compiler): a timer library and two exercises that blink LEDs with hardware timers and interrupts.

> Exercise 3 of the Embedded Systems course (1st year, 2nd semester), MSc Robotics Engineering, University of Genoa.

## Branches

Each exercise is in its own branch:

| Branch | Exercise |
|---|---|
| `ex3.1` | **Timer interrupt.** The main loop toggles LED 1 every 200 ms, polling Timer 1. At the same time, the Timer 2 interrupt (every 100 ms) drives LED 2, which stays off for 500 ms and on for 500 ms. |
| `ex3.2` | **External interrupt.** A button, remapped to the `INT1` external interrupt, enables and disables the blinking of the LED (200 ms period). When blinking is disabled, the LED stays off. |

## Content

- **`timer.c` / `timer.h`:** timer library used by both exercises.
  - `tmr_setup_period(timer, ms)`: configures Timer 1 or Timer 2 (prescaler 1:256) to expire every `ms` milliseconds, up to 200 ms.
  - `tmr_wait_period(timer)`: waits for the end of the current period, and returns 1 if the period had already expired (deadline missed).
  - `tmr_wait_ms(timer, ms)`: blocking delay of any length, split into periods of at most 200 ms.
- **`ex3.c`:** the exercise of the branch: pin configuration, interrupt setup and main loop.

## Usage

Open the folder as a project in **MPLAB X IDE** with the XC16 compiler, build it and program the board.
