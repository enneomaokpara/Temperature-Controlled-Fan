# Temperature-Controlled-Fan
An automatic cooling fan: a TMP36 temperature sensor feeds an Arduino Uno, which switches a DC motor (fan) on when the temperature crosses 28 °C and off when it drops back below. A miniature thermostat - the same sense → decide → actuate loop used in real thermal management.
**Status:** Designed, wired, and validated in simulation (Tinkercad Circuits).
## How it works
The TMP36 outputs 10 mV per °C with a 500 mV offset at 0 °C. The Arduino reads it on analog pin A0, converts to Celsius, and compares against a 28 °C threshold:

Temperature streams to the Serial Monitor every 500 ms.
## Design decisions
- **28 °C threshold:** comfortably above room temperature so the fan idles off, low enough to demo with the slider.
- **Direct pin drive:** in simulation the motor runs straight off D3. A physical build would use a transistor/MOSFET driver since a motor draws more current than a pin should source - noted, not hidden.
- **On/off control** instead of PWM speed ramping: simpler, and the threshold behavior is the point of the demo.
## Build log (Tinkercad Circuits)
1. Arduino Uno R3 + TMP36 + DC motor (no encoder) on the canvas.
2. TMP36: VCC→5V, Vout>AO, GND→GND (flat side
facing, left to right).
3. Pasted tempta in started simuDa
, started simulation.
## Validation (Tinkercad):

Threshold behavior confirmed in both directions.
## Expected vs. actual
**Expected:** fan follows the temperature slider across the threshold.
**Actual:** worked exactly as designed on the first run - no debugging needed. The main lesson was component selection: the plain DC motor (not the encoder version) is the right part for simple on/off control.
## Code
See 'temp_fan. ino'. Key conversion: 'tempc = (voltage - 0.5) × 100°
## Files
- Tinker Cad Screenshot
## Honest scope
Designed and simulation-validated by Emmanuella Okpara. 