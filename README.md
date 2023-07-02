# Modul

*Modul* is a proof-of-concept human-input-device platform for building modular
keyboards with pluggable modules.

## References

- [LTC4316](https://www.analog.com/media/en/technical-documentation/data-sheets/4316fa.pdf)
- [CH32V003](http://www.wch-ic.com/products/CH32V003.html)
- [CH32V103](http://www.wch-ic.com/products/CH32V103.html)
- [CH32V203](http://www.wch-ic.com/products/CH32V203.html)
- [CH32V303](http://www.wch-ic.com/products/CH32V303.html)
- [ch32-rs](https://github.com/ch32-rs)
- [Rust on the CH32V003](https://noxim.xyz/blog/rust-ch32v003/)

## Project Naming

> REDO THIS

```
┌─────────────┬─────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│  REFERENCE  │                               <MODULE>-<SEQUENCE>-<REVISION><PRODUCTION>                                │
├─────────────┴─────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│┌────────────────────────┬────────┐┌──────────┬─────────────────────┐┌──────────┬───────────────┐┌────────────┬───────┐│
││ MODULE                 │ SHORT  ││ SEQUENCE │ THE SEQUENCE NUMBER ││ REVISION │ THE REVISION  ││ PRODUCTION │ SHORT ││
│├────────────────────────┼────────┤├──────────┘ IS A SEQUENTUAL AND │├──────────┘ NUMBER IS A   │├────────────┼───────┤│
││ CORE                   │ CORE   ││ UNIQUE NUMBER IDENTIFYING THE  ││ PERPETUALLY INCREMENTING ││ PROTOTYPE  │ P     ││
││ HUMAN-INTERFACE-DEVICE │ HID    ││ VARIANT OF THE MODULE.         ││ IDENTIFIER FOR THE VER-  ││ CANDIDATE  │ C     ││
││ AUDIO                  │ AUDIO  │└────────────────────────────────┘│ SION OF THE HARDWARE.    ││ FINAL      │ F     ││
││ VISUAL                 │ VISUAL │                                  └──────────────────────────┘└────────────┴───────┘│
│└────────────────────────┴────────┘                                                                                    │
└───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

## Interconnect

The interconnector is a simple i2c/SMBus interface along with gnd and vcc
(undecided, but this will most likely be 3.3v). All connectors on boards are 90
degree 2.54mm pitch female headers, inset 1.27mm from the board edge as to allow
a male header to sit flush between two boards. The order of the pins from is `GND`,
`SDA`, `SCL`, `VCC`, `SCL`, `SDA` and `GND`. This makes the connector work from both
directions.

```
────┐      ┌─┐      ┌────
GND ┤   ───┼─┼───   ├ GND
SDA ┤   ───┼─┼───   ├ SDA
SCL ┤   ───┼─┼───   ├ SCL
VCC ┤   ───┼─┼───   ├ VCC
SCL ┤   ───┼─┼───   ├ SCL
SDA ┤   ───┼─┼───   ├ SDA
GND ┤   ───┼─┼───   ├ GND
────┘      └─┘      └────
```

## Modules

Modules communicate over i2c/SMBus.
