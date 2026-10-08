# The user IO is as follows:  

## Buttons
8 Buttons

| NET | FUNCTION | NOTE |
| --- | --- | --- |
| BTN_1 | UP | Also the Boot |
| BTN_2 | LEFT | --- |
| BTN_3 | PAUSE | --- |
| BTN_4 | DOWN | --- |
| BTN_5 | RIGHT | --- |
| BTN_6 | MENU | --- |
| BTN_7 | B | --- |
| BTN_8 | A | --- |

## Touch
2 Touch Strips, 5 zones each

| NET | FUNCTION | Relative Position |
| --- | --- | --- |
| TOUCH_8 | ZONE L1 | Top Left |
| TOUCH_7 | ZONE L2 | Left |
| TOUCH_6 | ZONE L3 | Middle Left |
| TOUCH_5 | ZONE L4 | Left |
| TOUCH_4 | ZONE L5 | Bottom Left |
| --- | --- | --- | --- |
| TOUCH_3 | ZONE R1 |Top Right |
| TOUCH_14 | ZONE R2 | Right |
| TOUCH_9 | ZONE R3 | Middle Right |
| TOUCH_2 | ZONE R4 | Right |
| TOUCH_1 | ZONE R5 | Bottom Right |


## Analog Volume
1 volume adjust knob

The volume adjust is a 0 to 10kOhm potentiometer, where 0 corresponds to minimum gain and 10k to maximum gain.


#Prototype

The Fairy Prototype used a different mapping as well as 4 additional Touch Button Zones

## Touch

| NET | FUNCTION | Relative Position | Device |
| --- | --- | --- | --- |
| TOUCH_1 | ZONE L1 | Top Left | ESP32 |
| TOUCH_2 | ZONE L2 | Left | ESP32 |
| TOUCH_9 | ZONE L3 | Middle Left | ESP32 |
| TOUCH_14 | ZONE L4 | Left | ESP32 |
| TOUCH_3 | ZONE L5 | Bottom Left | ESP32 |
| --- | --- | --- | --- |
| TOUCH_8 | ZONE R1 |Top Right | ESP32 |
| TOUCH_4 | ZONE R2 | Right | ESP32 |
| TOUCH_5 | ZONE R3 | Middle Right | ESP32 |
| TOUCH_6 | ZONE R4 | Right | ESP32 |
| TOUCH_7 | ZONE R5 | Bottom Right | ESP32 |
| --- | --- | --- | --- |
| TOUCH_21 | Touch Button | CH32 |
| TOUCH_M | Trihard Top Button | CH32 |
| TOUCH_A | Trihard Left Button | CH32 |
| TOUCH_G | Trihard Right Button | CH32 |