# CH32 Coprocessor
The Swadge has a CH32V003F4U6 as a coprocessor which handles the button IO.
BTN_1 has a discrete 10k Pullup resistor. All other buttons should have their GPIO pull up resistor enabled.
When the Swadge has USB Power the [Battery Charge Circuit](/docs/PDN.md#Charging) the BMS will provide two digital signals to the CH32. The Standby and Charge GPIO inputs should have their internal pull up resistors enabled. Charging is Active Low when the BMS is in the charging state. Standby is Active Low when the BMS reports the battery is fully charged. Both Charging and Standby being high level indicates either no 5V available or a BMS fault.
VMON measures the battery voltage. The Measurement circuit resistor devider has a gain of 2/3. Resulting in 5V actual resulting in 3.33V at the pin, equivalent to 205 counts per Volt. No pull up or pull down should be used on the VMON pin. The n0rmal battery operating range is from 4.2 to 3V.
Button Polling, Debounce, Voltage Measurement and its filering, should all be accomplished on the CH32.

## Pin Assignment for 2027 Fairy

| PIN | FUNCTION | NOTE |
| --- | --- | --- |
| 1 | BTN_1 / "UP" | GPIO PD7, Can be made reset pin |
| 2 | Unused | --- |
| 3 | Unused | --- |
| 4 | GND | --- |
| 5 | BTN_6 "Menu" | GPIO PD0 |
| 6 | 3V3 | --- |
| 7 | BTN_3 "Pause" | GPIO PC0 |
| 8 | STANDBY | GPIO PC1 |
| 9 | CHARGE | GPIO PC2 |
| 10 | BTN_4 "Down" | GPIO PC3 |
| 11 | VMON | ADC A2 |
| 12 | BTN_2 "Left" | GPIO PC5 |
| 13 | BTN_5 "Right" | GPIO PC6 |
| 14 | Unused | --- |
| 15 | CH32_COMMS | SWIO |
| 16 | BTN_8 "A" | --- |
| 17 | BTN_7 "B" | --- |
| 18 | Unused | --- |
| 19 | Unused | --- |
| 20 | Unused | --- |

## Pin Assignment for 2027 Prototype

Technical Demo for CH32 Touch Discrete Button Inputs - "M, A, G" Trihard, and "F" button implementation by toggling pullup/pulldown in conjunction with timer controlled ADC samples.


| PIN | FUNCTION | NOTE |
| --- | --- | --- |
| 1 | BTN_1 / "UP" | GPIO PD7, Can be made reset pin |
| 2 | Touch A | ADC A1 |
| 3 | TOUGH G | ADC A0 |
| 4 | GND | --- |
| 5 | BTN_5 "Right" | GPIO PD0 |
| 6 | 3V3 | --- |
| 7 | BTN_2 "Left" | GPIO PC0 |
| 8 | Unused | --- |
| 9 | BTN_4 "Down" | GPIO PC2 |
| 10 | Unused | --- |
| 11 | VMON | ADC A2 |
| 12 | CHARGE | GPIO PC5 |
| 13 | STANDBY | GPIO PC6 |
| 14 | BTN_6 "Menu" | GPIO PC7 |
| 15 | CH32_COMMS | SWIO |
| 16 | BTN_3 "PAUSE" | GPIO PD2 |
| 17 | BTN_8 "A" | GPIO PD3 |
| 18 | BTN_7 "B" | GPIO PD4 |
| 19 | TOUCH F | ADC A5 |
| 20 | TOUCH M | ADC A7 |