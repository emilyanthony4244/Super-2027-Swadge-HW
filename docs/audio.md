# Audio Subsystem

## Speaker

The Swadge provides an amplifier and Speaker
The Speaker is an FS-1340, 700mW @ 8ohm nominal. The speakers useful range is from 900Hz to 12kHz.

The Amplifier is an FM8002A.
Amplifier gain falloff begins at 10kHz and reaches -10dB at 50kHz, amplifier phase shift begins at 1kHz, reaches 30° at 10kHz, and 60° at 50kHz.
Nominal output power into an 8ohm load is 1.1W. To maintain THD and Noise Figures output power should be kept under 700mW
Amplifier Gain is set by the volume control knob [Battery Charge Circuit](/docs/PDN.md#Analog%20Volume). The Equation Avd = 2 x (Rf / Ri). Ri is a fixed 20kOhm resistor. Rf is adjustable from 0 to 10kOhm. This results in gain always being between 0 and 1.
Vpp should be aproximately 2.36Vac to result in 700mW output at full volume.

SPK_SHUTDOWN is an active low input which mutes the audio output and turns off the amplifier power stage when asserted.

The amplifier has a local 1uF and 22uF decoupling capacitor.

## Microphone
The microphone is a GMI4013S-2C30 omnidirctional electret condenser microphone. Its nominal resiting bias is 2V @ 0.5mA. However the Swadge uses it as a single ended input to an ADC channel, and instead biases it at 600mV @ 225uA resting.
A 4.7nF capacitor is placed in parallel with the microphone as a low pass filter. A 22uF capacitor and 33ohm resistor is placed on the microphone supply to decouple power supply noise.

## Aux
The Auxiliary Jack is designed for headphones and diverts the audio output from the speaker through the device plugged into it. The Aux return path is terminated with a 120 ohm resistor to ground.