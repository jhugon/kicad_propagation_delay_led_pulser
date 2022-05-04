# Propagation Delay LED Pulser Board in KiCAD

This KiCad board pulses an LED with a very short pulse. The pulse width is
defined by the propagation delay of 3 inverters.

Main power supply: 5 V
LED bias: 0-1.4 V

## Changelog

- v1.0 Difficult to hand-solder due to heat loss to ground plane (too many vias) and reversed 0612 capacitors
- v1.1 Remove extra vias and switch from 0612 to 1206 coupling caps

## Performance

### v1.1

Measured on 2022-05-04

Current draw not visible on power supply, so less than 10 mA

All measured with a 10x passive oscilloscope probe and ground clib hooked up to coax out:

- The clock coming out of the timer: 9.36 kHz
- The pulse coming out of the NAND gate:
  - Rise and fall times of 2 ns (may be probes)
  - Width of 11 ns
  - Baseline is 4.8 V
  - Pulse is 8 mV
- The pulse coming out of the coax driving inverters, going into R2:
  - A fair amount of ringing ~ 20%
  - Rise and fall times of 2 ns (see above)
  - Width of 11 ns
  - Baseline is -77 mV
  - Pulse is 5 V
- The LED anode:
  - Rise time: 2 ns
  - Fall time: ringing 8.5 ns
  - Width: 12 ns
  - Baseline: -77 mV
  - Pulse: 2.8 V

Pulse measurement of coax output into high-Z scope input:

- Rise time 2.48 ns
- Fall time 2.45 ns
- Width 11.61 ns
- Baseline -90 mV
- Pulse 4.6 V
- Ringing ~ 10%, damped out around 20 ns after pulse fall
