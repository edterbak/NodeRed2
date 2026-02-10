## Changes
Below are the changes in version 26.2.1 stable compared to 25.x stable

<ins>Major changes:</ins></br>
- WAR renamed to CCC. (from Dutch WeersAfhankelijkeRegeling to CustomCompensationCurve, which makes more sense)</br>
- Added generic [MQTT-command manager] function. It checks if commands are picked up by the Panasonic. If not it retries 3x
- Added a MQTT-command rate limiter to prevent/reduce panasonic dropping commands</br>
- Added support (control) for Zone 2</br>
- Added zone 2 support to CCC function</br>
- Added zone 2 support to RTC function</br>
- RTC Automations require a single target zone</br>
- Added support for buffer tank usage together with functions</br>
- Added support for P1 meters which reports different data types. (type 1 / 2)</br>
- Added extra external Link-In options. See right side of [WP Input]-tab. 

<ins>Other noteworthy changes:</ins></br>
- SoftStart function rewrite to accomodate for buffertank and multizone setups</br>
- Improved charts. Now surviving reboots</br>
- Allow sending HEAT setpoints in all operating modes</br>
- Removed all QOS 1 and 2 on mqtt nodes. It is not supported</br>
- Added more Panasonic pump versions to detect</br>
- Fan 2 auto-show/hide when it is detected</br>

********

<ins>Existing limitations:</ins></br>
- Cool function only works in DIRECT mode. (still on the list to fix, but is on low priority)
  
[Back to top](#index)
