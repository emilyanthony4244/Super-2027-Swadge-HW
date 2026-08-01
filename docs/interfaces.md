# Swadge Interfaces

The Swadge has the following interfaces:
USB 2.0 via J1, between the [CPU](/docs/CPU.md) and the USB port  
UART programming
SAO port, including two GPIO and I2C  
Audio Aux Port  

## USB

The USB 2.0 signal from the port to the CPU
Have an approximately 90 ohm differential impedance. It is recommended to achieve this with a tightly coupled routing and coplanar ground.
> Recommended 9.5 mil trace width with 5 mil spacing when coplanar ground is used.
The USB port to ESP32 trace length should be less than 2 inches
trace length must be less than 6 inches.
The USB lines should have termination resistors at the USB Jack.
The USB lines should have a total skew offset of less than 50ps

## I2C

The I2C_SDA and I2C_SCL lines should be routed with a total skew offset between them of no more than 200ps
It is recommended to have termination resistors at the furthest end of the I2C lines from the ESP32
It is recommended to run I2C lines through pads rather than stub them off to minimize all stub lengths. The SAO will by necessity be the longest stub.
