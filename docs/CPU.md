# Background
The Swadge is powered by an ESP32 module with integrated bluetooth antenna

# Pin Assignment ESP32-S3-WROOM-1-N16R8

## Fixed Assignment

The following IO is fixed by hardware constraints and cannot be reassigned

1 - Ground  
2 - 3V3 
3 - Chip Enable 
13 - USB(-)  
14 - USB(+)  
27 - Boot Pin
28 - Not Connected, Reserved for PSRAM  
29 - Not Connected, Reserved for PSRAM 
30 - Not Connected, Reserved for PSRAM 
37 - TXD0  
36 - RXD0  

## Pin Table

| Pin Number | IO | Use | Alternate Features | Notes |
| --- | --- | --- | --- | --- |
| 1 | Ground | Ground | N/A | --- |
| 2 | 3V3 | 3V3 | N/A | --- |
| 3 | EN | EN | N/A | --- |
| 4 | GPIO4 | TOUCH4 | ADC1_CH3 | --- |
| 5 | GPIO5 | TOUCH5 | ADC1_CH4 | --- |
| 6 | GPIO6 | TOUCH6 | ADC1_CH5 | --- |
| 7 | GPIO7 | TOUCH7 | ADC1_CH6 | --- |
| 8 | GPIO15 | SAO_A | XTAL_32K_P, ADC2_CH4 | --- |
| 9 | GPIO16 | SAO_B | XTAL_32K_N, ADC2_CH5 | --- |
| 10 | GPIO17 | MIC via ADC2_CH6 | ADC2_CH6 | --- |
| 11 | GPIO18 | TFT_RESET | ADC2_CH7 | --- |
| 12 | GPIO8 | TOUCH8 | ADC1_CH7| --- |
| 13 | GPIO19 | USB (-) | GPIO19, ADC2_CH8 | --- |
| 14 | GPIO20 | USB (+) | GPIO20, ADC2_CH9 | --- |
| 15 | GPIO3 | TOUCH3 | ADC1_CH2 | --- |
| 16 | GPIO46 | Unused  | --- | Strapping Pin |
| 17 | GPIO9 | TOUCH9 | GPIO9, ADC1_CH8 | --- |
| 18 | GPIO10 | FSPI_CS0 (LCD) | GPIO10, TOUCH10, & ADC1_CH9 | --- |
| 19 | GPIO11 | FSPID - TFT_SDA | GPIO11, TOUCH11, & ADC2_CH0 | --- |
| 20 | GPIO12 | FSPICLK - TFT_CLK | GPIO12, TOUCH12, ADC2_CH1 | --- |
| 21 | GPIO13 | TFTATP | GPIO13, TOUCH13, ADC2_CH2 | --- |
| 22 | GPIO14 | TOUCH14 | GPIO14, ADC2_CH3 | --- |
| 23 | GPIO21 | SLEEP | GPIO21 | --- |
| 24 | GPIO47 | SPK | GPIO47 | --- |
| 25 | GPIO48 | SPK_SHDN | GPIO48 | --- |
| 26 | GPIO45 | Unused | GPIO45 | N/A | Strapping Pin |
| 27 | GPIO0 | Boot / "Button UP"| GPIO0 | Strapping Pin for Boot Source |
| 28 | GPIO35 | Not Connected | GPIO35 | Reserved for Octal SPI PSRAM |
| 29 | GPIO36 | Not Connected | GPIO36 | Reserved for Octal SPI PSRAM |
| 30 | GPIO37 | Not Connected | GPIO37 | Reserved for Octal SPI PSRAM |
| 31 | GPIO38 | TFT_RS | GPIO38 | --- |
| 32 | GPIO39 | CH32_COMMS | GPIO39 | --- |
| 33 | GPIO40 | I2C_SDA  | GPIO40 | --- |
| 34 | GPIO41 | I2C_SCL  | GPIO41 | --- |
| 35 | GPIO42 | LED | GPIO42 | --- |
| 36 | RXD0 | RXD0 | GPIO44 | --- |
| 37 | TXD0 | TXD0 | GPIO43 | --- |
| 38 | GPIO2 | TOUCH2 | GPIO2 & ADC1_CH1 | --- |
| 39 | GPIO1 | TOUCH1 | GPIO1 & ADC1, CH2 | --- |
| 40 | GND | GND | --- | --- |
| 41 | GND | GND | --- | --- |

# Basic Operation

## BOOT
When the ESP32 Module first receives power, it enters its Chip Reset State. The Chip Reset State can also be induced by using a physical tool to short EN (PIN 3) to ground. The recommended way of doing this is by shorting C13 with a screwdriver if removal of the battery is not desired.

In the Reset State the status of the four strapping pins combined with the e-fuses determine the boot configuration.

Chip Boot Mode is determined by GPIO0 and GPIO46.
GPIO0 has a default weak internal pull up as well as a 10k external pull up via R12. GPIO0 can be pulled low by holding the "UP" button during the boot initialization. 
GPIO46 has a default weak internal pull down, and is otherwise unused on the Swadge. It should always be held low on Reset.

When GPIO0 is High, its default state, the ESP32 boots from its SPI flash memory.
When GPIO0 is Low, it enters download boot mode. In this mode the ESP32 will boot via USB, Serial, or JTAG.

## SLEEP
When Pin 23 is pulled low by the power switch the ESP32 is pulled into ULP deep sleep.
The Power Management Unit is operating any time the chip has power.
The ESP32 has four predefined power modes: Active, Modem Sleep, Light Sleep, and Deep Sleep

### Deep-Sleep
When in deep sleep the system is running on its internal RC_SLOW_CLK. Only select RTC ULP peripherals are available.

### Light-Sleep
When in light sleep the high speed clock and CPUs are not running, but the digital system retains the memory state to resume operation.

### Modem-Sleep
When in modem sleep everything is operating except the analog RF radio circuits.

## Watchdogs
There are four watchdog times:
Super Watchdog (SWD), RTC Watchdog (RWDT), and Two Main System Watchdogs (MWDT0 & MWDT1)

### Analog Super Watchdog
The SWD is a base analog timer that must be reset every second by the ULP coprocessor or the ESP32 will enter the [Reset State](#boot). The SWD has an interrupt register that will indicate a request aproximately 100ms before the SWD expires.

### Digital Watchdog
RWDT, MWDT0, and MWDT1 are 32 bit counters which have four programable trigger points. Each trigger point can select from the following actions: Disabled, Interrupt, CPU Reset (Of a single processor), and Core reset. RWDT additionally has access to the action of [System Reset](#boot). By default, stage 0 for RWDT is set to system reset during the initial boot process, to allow for automatic recovery.

# Ultra Low Power Coprocessor

# RISC Processor Cores

# PERIPHERALS

## UART

## I2C

## SPI

## LED PWM

## Touch Sensing

## ADC
