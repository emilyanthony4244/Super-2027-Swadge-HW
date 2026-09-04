# Background
The Power Distribution Network is the subsystem responsible for generating all applicable global voltage rails from the available power sources.
The global power rails are “GND” and “3V3”
The available power sources are “5VIN” and “V_BATT”
Local power rails are “2V8_LCD”, “TFT_LED”

| Net | Description | Interface |
| --- | --- | --- |
| GND | Global Ground Net, common return path for all portions of the swadge with the exception of the isolated BATT_N | Global |
| 3V3 | Global 3.3V DC power supply | Global |
| 5VIN | USB Supplied 5V DC, Used to either power the swadge or to recharge the onboard battery | J1 |
| BATT_P | Battery Positive Voltage | --- |
| BATT_N | Battery Negative Voltage, U4 Isolates the battery return from global ground when 
| LCD28 | 2.8V Display Logic Power | --- |
| TFT_LEDA | PWM Display Backlight Power | --- |

# Requirements
The PDN shall accept a nominal 5V DC from USB input J1
The PDN shall provide power from the USB source when 5VIN is in the range of 4.35VDC to 5.5VDC.
The PDN shall accept a range of voltage from the battery(s) between 2.4V and 5.5V.
The PDN shall generate a regulated 3.3V DC from a range of input voltages for both battery and USB operation
The PDN should minimize both conducted and radiated EMI and its effects on other subsystems of a Swadge and external items.

# Implementation
## Auctioneering
The [3.3V Regulator] (#3V3) is fed from an auctioneered supply via Q2. Q2 and D22 passively switch the source to the system to whichever has the higher voltage. The total system current passes through fuse F1.

## 3V3  
The 3.3Vdc power is regulated by an aerosemi MT3410 synchronous switching regulator. The MT3410 is a SOT23-5 Package integrated switch and controller. The Feedback reference is 0.6V. The regulator is rated to operate from 2.3 up to 6V input voltage. The control has a 1.9V undervoltage lockout. As Vin drops to the regulator setpoint the control shifts from switching buck to LDO mode. The switching frequency is nominally 1.2MHz.  
A 2.2uF switching inductor is used. The FB network is set up with a 10k and a 43k, for a 10/53 reduction on the Vout to produce a nominal 3.18V output before accounting for component error. The component datasheet recommends a 10uF ceramic capacitor on both the input and output. In the Swadge Prototype a 1uF input capacitor was used and a 1uF paired with a 22uF output capacitor was used.

## Charging
USB Power is provided to the charging circuit in parallel to the system. A TP4056 BMS regulates VBATT to maintain a correct charge profile. an NTC thermistor is used to provide temperature feedback and limit charging in abnormal temperature conditions. The Charging circuit provides two status LEDs for Charging and Standby, as well as digital inputs to the CH32 coproessor. When the USB port is not providing power, the charging system is not active. 
