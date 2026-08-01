# Background
The Power Distribution Network is the subsystem responsible for generating all applicable global voltage rails from the available power sources.
The global power rails are “GND” and “3V3”
The available power sources are “5V_USB” and “V_BATT”
Local power rails are “2V8_LCD”, “TFT_LED”
Intermediate power rails include “VSYS”

| Net | Description | Interface |
| GND | Global Ground Net, common return path for all portions of the swadge with the exception of the isolated BATT_N | Global |
| 3V3 | Global 3.3V DC power supply | Global |
| 5V_USB | USB Supplied 5V DC, Used to either power the swadge or to recharge the onboard battery | J1 |
| 2V8_TFT | Display

# Requirements
The PDN components should all be prefixed by a number 2, in the format of 2x, or 2xx
The PDN shall accept a nominal 5V DC from USB input J1
The PDN shall provide power from the USB source when 5V_USB is in the range of 4.35VDC to 5.5VDC.
The PDN shall accept a range of voltage from the battery(s) between 2.4V and 5.5V.
The PDN shall generate a regulated 3.3V DC from a range of input voltages for both battery and USB operation
The PDN should minimize both conducted and radiated EMI and its effects on other subsystems of a Swadge and external items.
