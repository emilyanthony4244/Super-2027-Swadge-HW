# Background
The Swadge is powered by an ESP32 module with integrated bluetooth antenna

# Pin Assignment ESP32-S3-MINI-1-N4R2

## Fixed Assignement

The following IO is fixed by hardware constraints and cannot be reassigned


1 - Ground  
2 - Ground  
3 - 3V3  
4 - Boot Pin, used to boot over UART instead of ROM. Traditionally connected to BUTTON1 "UP"  
23 - USB(-)  
24 - USB(+)  
26 - Not Connected, Reserved for PSRAM  
39 - TXD0  
40 - RXD0  
42 - Ground  
43 - Ground  
45 - Enable  
46-65 - Ground  

## Firm Assignment

The following IO is constrained by the IO peripherals of the ESP32  
Pins 5 - 18 are Touch Inputs, 5 - 16 have been selected as TOUCH1 through TOUCH12  
Pins 19 & 20 are used for the RTC crystal if onboard RTC is used.  

## Note on TFT_FMARK

TFT_FMARK is meant to reduce screen tearing. If this function is not required it would be better used for the expansion slot FSPI_WPI input. However during normal use the FSPI_WP signal would only be used during initial flashing to load static art assets, and can be accomplished as part of the flashing jig.

## _WIP_ Pin Table

| PIN | Default | 2027 Assignment | Blocked Functionality | Note |
| --- | --- | --- | --- | --- | --- |
| 1 | Ground | Ground | N/A | --- |
| 2 | Ground | Ground | N/A | --- |
| 3 | 3V3 | 3V3 | N/A | --- |
| 4 | GPIO0 | Boot / "Button UP" | N/A | Strapping Pin |
| 5 | GPIO1 | TOUCH1 | ADC1_CH0 | --- |
| 6 | GPIO2 | TOUCH2 | ADC1_CH1 | --- |
| 7 | GPIO3 | TOUCH3 | ADC1_CH2 | --- |
| 8 | GPIO4 | TOUCH4 | ADC1_CH3 | --- |
| 9 | GPIO5 | TOUCH5 | ADC1_CH4 | --- |
| 10 | GPIO6 | TOUCH6 | ADC1_CH5 | --- |
| 11 | GPIO7 | TOUCH7 | ADC1_CH6 | --- |
| 12 | GPIO8 | TOUCH8 | ADC1_CH7 | --- |
| 13 | GPIO9 | TOUCH9 | ADC1_CH8 & FSPI | --- |
| 14 | GPIO10 | TOUCH10 | ADC1_CH9 & FSPI | --- |
| 15 | GPIO11 | TOUCH11 | ADC2_CH0 & FSPI | --- |
| 16 | GPIO12 | TOUCH12 | ADC2_CH1 & FSPI | --- |
| 17 | GPIO13 | VMON via ADC2_CH2| FSPI | --- |
| 18 | GPIO14 | SPK | TOUCH14 & FSPI | --- |
| 19 | GPIO15 | RTC_P | ADC2_CH4 | --- |
| 20 | GPIO16 | RTC_N | ADC2_CH5 | --- |
| 21 | GPIO17 | SPK_SHDN | ADC2_CH6 & UART1 | --- |
| 22 | GPIO18 | MIC via ADC2_CH7 | ART1 | --- |
| 23 | GPIO19 | USB (-) | ADC2_CH8 | --- |
| 24 | GPIO20 | USB (+) | ADC2_CH9 | --- |
| 25 | GPIO21 | SAO_A | None | --- |
| 26 | GPIO26 | Not Connected, Reserved | N/A | Reserved for SPICS1 (PSRAM) |
| 27 | GPIO47 | TFT_RESET | N/A | --- |
| 28 | GPIO33 | SAO_B | GPIO33 | --- |
| 29 | GPIO34 | FSPI_CS0 (TFT) | GPIO34 | --- |
| 30 | GPIO38 | TFT_RS | N/A | --- |
| 31 | GPIO35 | FSPI_D | GPIO35 | --- |
| 32 | GPIO36 | FSPI_CLK | GPIO36 | --- |
| 33 | GPIO37 | FSPI_Q | GPIO37 | --- |
| 34 | GPIO38 | TFT_FMARK _or_ FSPI_WP | FSPI_WP | --- |
| 35 | GPIO39 | FSPI_CS1 (EXP) | JTAG MTCK | --- |
| 36 | GPIO40 | TFT_ATP | JTAG MTDO | --- |
| 37 | GPIO41 | I2C_SDA | JTAG MTDI | --- |
| 38 | GPIO42 | I2C_SCL | MTMS JTAG | Strapping Pin |
| 39 | TXD0 | TXDO | GPIO43 | --- |
| 40 | RXD0 | RXD0 | GPIO44 | --- |
| 41 | GPIO45 | SWIO | None | Strapping for VDD_SPI |
| 42 | Ground | Ground | None | --- |
| 43 | Ground | Ground | None | --- |
| 44 | GPIO46 | LED | None | Strapping Pin |
| 45 | EN | EN | None | --- |
| 46-65 | Ground | Ground | None | --- |
