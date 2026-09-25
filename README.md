# A053 F0f/F0r amplifier adapter (design draft)

**Status: UNROUTED / NOT FABRICATION READY. Do not order PCB from this draft.**

Goal: Convert Rokuhan A053 F0f/F0r (LOW=ON, 5 V HIGH=OFF) into open-collector low-side sink outputs with two NOT gates and one FMG3A dual digital transistor.

- U1: 74LVC2G04 dual inverter, 5 V supply.
- Q1: FMG3A two-channel transistor array.
- R1/R2: 47 kΩ pull-ups from F0f/F0r inputs to +5 V, 0603.
- C1: 100 nF (0.1 µF) decoupling, 0603, next to U1.
- C2: nominal 47 µF bulk capacitor provision, 1206 / 3216 metric, parallel with C1 between +5 V and GND.
- Common ground; COM+ stays wired directly on the lighting side and is NOT present on this adapter PCB.

## PCB interface (six solder pads, no COM+)

| Pad | Net | Direction / purpose |
| --- | --- | --- |
| J1.1 | VCC_5V | Input: regulated +5 V from A053 (NOT DCC track voltage or 12 V) |
| J1.2 | GND | Input: A053 logic ground; common with the external lighting circuit negative return |
| J1.3 | F0f_IN | Input: A053 forward function, LOW = ON |
| J1.4 | F0r_IN | Input: A053 reverse function, LOW = ON |
| J2.1 | F0f_OUT | Output: open collector sink, ON -> GND, OFF -> high impedance |
| J2.2 | F0r_OUT | Output: open collector sink, ON -> GND, OFF -> high impedance |

J2 does not need a duplicate GND pad; GND returns through J1.2. If wiring topology needs a second GND connection, revise explicitly rather than assuming COM+. Use approximately 0.20-0.25 mm for low-current signal traces, a wider approximately 0.5 mm GND return where geometry permits, and a stitched ground plane. No pull-up from F0 outputs to +5 V. Outputs are **not** sources of 5 V or COM+.

**Implementation note:** Existing uncommitted KiCad draft still has an extra J2 GND pad and is unrouted; this README specifies the agreed six-pad revision, not a completed PCB.

C2 footprint does not guarantee the fit or effective capacitance of any 47 µF MLCC. Select an actual part and verify land pattern, DC-bias derating, voltage rating, clearance and A053 5 V rail inrush/startup limits.

**Design files are not yet committed to this branch.** The existing local KiCad ZIP is an unverified placement draft, not a routed production PCB. Check schematic/footprint pin maps, library validity, KiCad import, ERC/DRC, clearances and routing before producing any Gerbers.
