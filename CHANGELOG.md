# Changelog

## [HW v1.1]
### Added
- Added voltage monitoring `MAX11617` for AFE board
- Added LEDs for `P12V0 TIA_VCC` and `P1V8`
- Added cable support mounting holes

### Fixed
- Unused signals to `GND` on AFE connector
- Added `VREF` buffers for `DACs` as new reference voltage (removed `IC2` 2.048V ref voltage)
- Corrected I2C addressing between FMC and AFE boards on dedicated I2C interface. On AFE changed addressing of `EEPROM (IC37)` and `LM75(IC28, IC33)`
- `nOE` connected to `GND` for `SN74LV595` (calibration pulses)
- `SC18IS602` is now replaced with `SC18IS606PWJ`, so the signals are rerouted and needs to be updated: `DAC and CAL signals` (as per #2 issue; `CAL_ON` removed, `DAC_ADR2` line moved to another chip)
- `SN74LV595` changed control and interface signals; `SRCLK and RCLK` are now divided. `SRCLK` is for writing to registers, the `RCLK=CAL_ON` and copies the registers to internal buffers. `nOE` is now always at `GND`.
- `CAL_ON` now controlled directly from FPGA, removed from `SC18IS602 (IC31)`

[HW v1.1]: https://github.com/elhep/GEM_AFE_128/tree/v1.1
