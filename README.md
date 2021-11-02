## Grbl Firmware for OpenPnP

![File](img/arduino.png)

### Features
 - Dual Y axis
 - PWM output to control an Remote Control (RC) Servo for Drag Feeder
 - Two switches for Vacum and LED
 - Support for M114 and M115
 - Limit switch free design with Soft Limits on 3 axes after visual homing (optional)
 - Forked from GRBL_VERSION "1.1h" GRBL_VERSION_BUILD "20190830"


### A Machine in Action
https://user-images.githubusercontent.com/26599790/117642339-12d76100-b17f-11eb-941d-1dac84b9935f.mp4

### Wiring Diagram

![File](img/arduino_wiring.jpg)



### Repurposed GCodes
Function | Command
----|-----
RC Servo Power  | M3 - On, M5 - Off
RC Servo Positon | S30 - raise, S90 - lower
Vacum  | M8 - On, M9 - Off
LED | M7 - On, M10 - Off

### GCode Driver Commands

Setting | GCode
----|-----
CONNECT_COMMAND | G21 ; Set millimeters mode <br> G90 ; Set absolute positioning mode <br>M114 ; to sync grbl and openPnP
HOME_COMMAND | $H; <br>G92 X0 Y0 Z0
MOVE_TO_COMMAND | G0 {X:X%.4f} {Y:Y%.4f} {Z:Z%.4f} {Rotation:C%.4f} F{FeedRate:%.0f}
MOVE_TO_COMPLETE_COMMAND |G4 P0; Wait for moves to complete before returning
COMMAND_CONFIRM_REGEX | ^ok.*
POSITION_REPORT_REGEX | <WPos:(?<x>-?\d+\.\d+),(?<y>-?\d+\.\d+),(?<z>-?\d+\.\d+),(?<rotation>-?\d+\.\d+)>
COMMAND_ERROR_REGEX  | ^Crash.*

#### Credits

Grbl is an open-source project fueled by the free-time of our intrepid administrators and altruistic users. If you'd like to donate, all proceeds will be used to help fund supporting hardware and testing equipment. Thank you!
[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CUGXJHXA36BYW)

This work extensively uses code from Bob Beattie's OpenPnP-Grbl
