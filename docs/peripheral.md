# Summary

The Swadge has many peripherals to enhance user exierpience

# Lightning

The Swadge lighting is performed with WS2812 side firing individually addressable RGB LEDs.  
(Note - C5446701 lists a min VDD of 3.7Vdc but we run them at 3.2). 
Each LED acts as a serial shift register with 24bits of RGB data. They are daisy chained together.

# Inertial Measurement Unit

The Swadge has an IMU to detect motion of the device. The IMU reports its measurements over the I2C bus. The IMU has a fixed I2C address of 0x6A

