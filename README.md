# A053 F0f/F0r amplifier adapter (design draft)

**Status: UNROUTED / NOT FABRICATION READY. Do not order PCB from this draft.**

Goal: Convert Rokuhan A053 F0f/F0r (LOW=ON, 5 V HIGH=OFF) into open-collector low-side sink outputs with two NOT gates and one FMG3A dual digital transistor.

- U1: 74LVC2G04 dual inverter, 5 V supply.
- Q1: FMG3A two-channel transistor array.
- R1/R2: 47 kΩ pull-ups from F0f/F0r inputs to +5 V, 0603.
- C1: 100 nF (0.1 µF) decoupling, 0603, next to U1.
- C2: nominal 47 µF bulk capacitor provision, 1206 / 3216 metric, parallel with C1 between +5 V and GND.
- Common ground; COM+ must be supplied separately.

C2 footprint does not guarantee the fit or effective capacitance of any 47 µF MLCC. Select an actual part and verify land pattern, DC-bias derating, voltage rating, clearance and A053 5 V rail inrush/startup limits.

**Design files are not yet committed to this branch.** The existing local KiCad ZIP is an unverified placement draft, not a routed production PCB. Check schematic/footprint pin maps, library validity, KiCad import, ERC/DRC, clearances and routing before producing any Gerbers.
