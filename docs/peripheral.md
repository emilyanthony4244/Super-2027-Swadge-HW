# Summary

The Swadge has many peripherals to enhance user expierience

## Lighting

The Swadge lighting is performed with SK6812 side firing individually addressable RGB LEDs.  
Each LED acts as a serial shift register with 24bits of RGB data. They are daisy chained together.
The order is {G7 -> G0} {R7 -> R0} then {B7 -> B0}. The CPU must shift out the bits in reverse order from MSB (G7) to LSB (B0) per LED. The CPU must shift out the individual LED commands in reverse order, from D14 to D1.
The final LED frame buffer is 42 bytes in length, and is shifted out onto the line from Bit G7 of LED D14 through big B0 of LED D1.

## Inertial Measurement Unit

The Swadge has an IMU to detect motion of the device. The IMU reports its measurements over the I2C bus. The IMU has a fixed I2C address of 0x6A

## SAO

There is an Swadge Add-On connector
