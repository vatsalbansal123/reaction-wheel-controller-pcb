# Reaction Wheel BLDC Motor Control PCB

A compact, single-board controller for a brushless DC (BLDC) reaction wheel.

### Board at a glance

| | |
|---|---|
| **MCU** | STM32G431CBTx (Cortex-M4F, LQFP-48) |
| **Gate driver** | DRV8311H three-phase BLDC driver |
| **Communication** | CAN (SN65HVD231) + USB 2.0 (USB-C) |
| **Power input** | USB-C 5 V and screw-terminal motor supply |
| **Layers** | 2-layer copper (F.Cu / B.Cu) |
| **Outline** | ~48.6 × 49.5 mm, rounded corners (R2.5), four M2 corner mounting holes (H1–H4) |
| **Designed with** | KiCad 10 |

## Schematic

![Schematic](docs/reaction-wheel-bldc-motor-control-pcb.svg)

## PCB

| Top | Bottom |
|-----|--------|
| ![PCB top view](docs/pcb-top.png) | ![PCB bottom view](docs/pcb-bottom.png) |

## Key Components

| Reference | Part | Function |
|-----------|------|----------|
| U2 | STM32G431CBTx | Cortex-M4 motor-control MCU (LQFP-48) |
| U4 | DRV8311H | Three-phase BLDC gate driver / motor driver |
| U3 | AS5047D | Magnetic rotary position (angle) sensor |
| U5 | SN65HVD231 | CAN transceiver |
| U6 | TPS562200 | Step-down (buck) converter |
| U1 | USBLC6-2SC6 | USB ESD protection |
| D3 | NUP2105L | CAN bus ESD protection |
| Y1 | 16 MHz crystal | MCU clock source |
| J4 | USB-C receptacle | Power + USB 2.0 data |
| MT1 | Phoenix screw terminal | Motor power input |

### Connectors & I/O

- **J4** — USB-C (USB 2.0 + power)
- **MT1** — 2-pin screw terminal (motor phases / power)
- **J1** — 1x4 header, CAN (CAN_H / CAN_L)
- **J5** — 1x4 header, I²C (SDA / SCL)
- **J2** — 1x4 header, SWD debug (CLK / IO)
- **J6** — 1x6 header, SPI (CS / SCK / MISO / MOSI)
- **J3** — 1x3 pin header
- **SW1** — SPST tactile button

### Passives & Discretes

- **Capacitors:** 10n, 10p, 100n, 0.1u, 1u, 4.7u, 10u, 22u (0805 SMD)
- **Inductors:** 2.2u (0402), 120R ferrite bead (FB1)
- **Resistors:** 5k1, 10k, 30.1k, 47k, 100k (0402 / 0603 SMD)
- **Diodes:** SS34 Schottky (D1, D2)

> A full bill of materials can be regenerated from the schematic with:
> ```
> kicad-cli sch export bom reaction-wheel-bldc-motor-control-pcb.kicad_sch -o bom.csv
> ```

## Design Files

- `reaction-wheel-bldc-motor-control-pcb.kicad_sch` — schematic
- `reaction-wheel-bldc-motor-control-pcb.kicad_pcb` — PCB layout
- `reaction-wheel-bldc-motor-control-pcb.kicad_pro` — KiCad project

Designed with **KiCad 10**.
