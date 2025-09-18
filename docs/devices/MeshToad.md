# MeshToad

Meet MeshToad 🐸
A Meshtastic-compatible LoRa radio for your (Linux) computer.

![MeshToad v1.2 picture](/static/MeshToad_v1.2.jpg){ width="60%" }

Designed by MtnMesh community organizers [wehooper4](https://github.com/wehooper4) and [vid](https://github.com/vidplace7) (Austin).

## Warning

This board draws up to **900mA** (peak) during transmit, exceeding the USB 1.0/2.0 spec, please provide supplemental power in these cases, or reduce TX power.

## Features

- Use with `meshtasticd` to turn any Linux computer into a Meshtastic node.
- 1W (30 dBm) **TX**
- LNA for increased *RX* sensitivity
- Onboard EEPROM for automatic configuration (meshtasticd 2.6.5+)
- USB-C interface

MeshToad `v1.x` is [Open Hardware](https://oshwlab.com/mtnmesh/meshtoad-v1-2) (CERN Open Hardware Licence Version 2 - Strongly Reciprocal)

## Flashing

**Note**: MeshToads purchased from the creators (wehooper4 / vid) are generally pre-flashed 👍

Check out the guide: [Flashing the MeshToad or MeshTadpole](../guides/flash-meshtoad-meshtadpole.md)
