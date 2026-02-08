# NodeRed_Heishamon_control

_Main branch:_ https://github.com/edterbak/NodeRed_Heishamon_control ( = latest STABLE version (25.02))  
_Please look at the beta branch:_ https://github.com/edterbak/NodeRed_Heishamon_control/tree/25.06-BETA  
This is the latest active development, which is currently pretty stable already...

---

## Table of Contents

1. [Overview](#overview)  
   1.1 [About v25.02 Stable](#about-v2502-stable)  
   1.2 [SoftStart Note](#softstart-note)  
2. [What can this Node Red flow do for you?](#what-can-this-node-red-flow-do-for-you)  
3. [Requirements](#requirements)  
   3.1 [What do I need to make use of this flow?](#what-do-i-need-to-make-use-of-this-flow)  
   3.2 [Requirements on the Node Red install](#requirements-on-the-node-red-install)  
4. [Installation](#installation)  
   4.1 [Flow installation](#flow-installation)  
   4.2 [Dashboard & Flows URLs](#dashboard--flows-urls)  
   4.3 [How to personalize or customize](#how-to-personalize-or-customize)  
   4.4 [How to create a backup of your current flow](#how-to-create-a-backup-of-your-current-flow)  
   4.5 [How to update to a newer version](#how-to-update-to-a-newer-version)  
5. [Features](#features)  
   5.1 [Pumpspeed](#pumpspeed)  
   5.2 [WAR](#war)  
   5.3 [RTC](#rtc-room-temperature-correction)  
   5.4 [SoftStart](#softstart)  
   5.5 [SoftStart Quietmode](#softstart-quietmode)  
   5.6 [Solar²DHW](#solar²dhw)  
   5.7 [Scheduler](#scheduler)  
   5.8 [Conditions](#conditions)  
6. [Usage: The Dashboard](#usage-the-dashboard)  
   6.1 [Home](#home)  
   6.2 [Settings](#settings)  
   6.3 [Charts](#charts)  
       - [Temperature](#temperature)  
       - [Energy](#energy)  
       - [Degree Days](#degree-days)  
   6.4 [System](#system)  
7. [FAQ](#faq)  
8. [Release changelog](#release-changelog)

---

## Overview

### About v25.02 Stable

Personal note: There is a lot of time in between version 24 and 25 now. This does not mean my enthusiasme has decreased. Only my available time has decreased a lot. I still enjoy and support this project and will continue to do so here on Github and via the (Dutch) tweakers.net forum. I even have ambitions to add a (KIS) WAF friendly HA dashboard, but this has still yet to solidify and take off...

Anyway, this flow version works best with heishamon firmwares from 3.1 or higher. It is tested and working with fw3.9. From fw3.1+ there are new additional topics available of which two are used in the flow. I have been using fw3.9 for months now without any issues. For fw 2.0 there is a manual override available for the new topics [SYSTEM] > [HARDWARE] > Zone 1. But This flow will work with fw2.0, fw3.0 as well after these two topics have been set. However; It is adviced to update the firmware though. Here is a list of up-to-date firmware's for heishamon. https://github.com/Egyras/HeishaMon/tree/master/binaries

### SoftStart Note

There are also some breaking changes in the SoftStart function. Please read the tooltips from the menu items to set it correctly.

---

## What can this Node Red flow do for you?

Only using the default room controller does not let you see historical data easily. This controller is not extremely user friendly as well. This Node Red dashboard offers a lot of ease for that with charts and bar-charts. Additionally, I have built in a lot of extra functions to do specific tasks or automation's. More about that below...

---

## Requirements

### What do I need to make use of this flow?

The heishamon module working with your heat pump.  
A functional MQTT broker. (Mosquitto / HiveMQ / EMQX /etc.)  
A functional Node Red instance.

1. Obviously, you need the heishamon pcb module connected to your heat pump and have it functional. Without this module, you can stop reading. 😄 See this site to get one: https://www.tindie.com/stores/thehognl/  
2. You can use any broker that is 24/7 available. You can install it on any system, as long as heishamon and the broker can communicate with each other and the Node Red can communicate with the broker.  
3. You can install node red on a lot of devices. It can be directly on Linux or a device like Raspberry Pi. You can also run it in a container (self hosted) or within Home Assistant (add-on). For all options see: https://nodered.org/  
   All of these options are good, as long as the Node Red application can communicate with the broker and the Node Red instance has persistent storage enabled.

The Node Red flow is stand-alone so:  
You do not require a database.  
You do not require HomeAssistant.  
If you have HomeAssistant also connected to heishamon >> Disable all related automation's!! 2 captains on 1 ship does not go well....

### Requirements on the Node Red install:

Details

---

## Installation

### Flow installation

Details

### Dashboard & Flows URLs

Dashboard: `http://IP:1880/ui`  (For HomeAssistant: `http://IP:1880/endpoint/ui`)  
Flows: `http://IP:1880/#flow`

### How to personalize or customize

Details

It is advised to create a separate tab for your external sources. Any source available in Node Red can be conditioned and used as a sensor in the functions. If you do this in an 'personal tab', then it is likely easier to update later to newer versions. (no guarantees of course)

### How to create a backup of your current flow

Details

There is no easy solution currently know by me to update only changed nodes or flows.  
First: Create a backup of current version.  
Select all tabs by holding CTRL. Then in the right menu select Export > Download.

### How to update to a newer version

Details

Update to newer version:  
I found it is easiest to:  
1, remove the tabs, WP MQTT, WP Dash, WP Control, WP Solar, WP Scheduler completely  
2, remove all ui_base, ui_group and ui_tab references from the flows. *Keep the MQTT (x.x.x.x) and Home Assistant references.  
3, import new version  
4, correct setup, eg. MQTT server.  
5, re-connect your personalization’s. *Not nessesary if you used a WP_Personal tab (see FAQ.md).

If there are better ideas about this, please inform me.

---

## Features

### Pumpspeed

This function allows you to set dynamic pump speeds, depending on the current operation.  
Set a different maximum water flow during DHW operation.  
Set a different maximum water flow during HEAT operation.  
You can set a default (low) maximum water flow. This is active when both operations are inactive (with active compressor).

Note: Do not set the maximum flow too low. It causes irratic behavior and a LOT of stop/starts.

### WAR

weather dependent temperature control.  
This function is only available when the heat pump is set to "Direct" mode. When the heat pump is set to "Compensation Curve" mode, the WAR function is automatically greyed out and disabled.

**Question:** Why have you created the same custom function while Panasonic provided the same function as "Compensation Curve"?  
**Answer:** The native Panasonic implementation is limited to the in-built thermocouple or connected external temperature sensor. Both are affected by direct sunlight and show incorrect values then. The custom function is able to use any sensor which is able to produce values into Node Red. Personally I use "OpenWeatherMap" as a source. But any local sensor can be used. You can import / export settings to the panasonic heat pump.

### RTC (Room Temperature Correction)

This function adjusts the setpoint of the water depending on the room temperature. When the temperature in a room gets too high, it will add "-1" to the current setpoint of the water temperature or shift.  
You can set the room target temperature, the temperature limits and you can set the correction to be performed.  
Additionally it is possibility to use automation's. To have the pump shut down when above a trigger temperature and turn back ON again below a revert temperature.

### SoftStart

Default behavior of the heat pump is when it starts up the compressor will go to high Hz for a period. Only when the returning water temperature approaches the setpoint, it ramps down the Hz and get more economic.  
If the SoftStart function is enabled and the compressor starts, the water setpoint will be lowered. This should cause the compressor to ramp the compressor down quicker, within minutes.  
When ramp down of the compressor frequency has occurred, the HEAT setpoint restrictions will gradually be lifted.

There's an add-on to the SoftStart called SoftStart-Quietmode

### SoftStart Quietmode

This is an extra (add-on) function to reduce the compressor frequency at startup even more. Some heat pump models will start a run and always go up to 45 Hz in de first minute (s) regardless of the target temperature.  
This Quietmode (when switched on) will put the heat pump in the Quietmode (level 3) at rest and waits till the run starts. When the compressor turns on, the Quietmode will remain active for an amount of time and after this time switches back to the previous Quietmode (if set).  
You can specify this fallback time in the Setup - Quietmode time (default 5 min).

### Solar²DHW

The aim of this function is to increase efficiency (and save cost) by utilizing solar energy as much as possible.  
When there is solar energy in abundance, you can tell the heat pump to use that energy to heat up your DHW water tank.  
To determine if there is enough solar energy, you need any form of power measurement. This can be a P1 power meter, or a meter directly behind your panels.

### Scheduler

You can enable/disable a schedule, multiselect a day of the week, specify the time (hour + minute) and give the schedule a name.  
I have added an option to create 10x schedules for the following actions:

- Toggle heat pump power on / off  
- Set water setpoint (heat shift / heat direct)  
- Set room setpoint (RTC function)  
- Start Force DHW runs  
- Start Sterilization runs  
- Set Quiet modes  
- Set operating modes  
- Toggle a custom function on / off

On each line of the scheduler, you can indicate if the heat pump should be powered on for the task or not.  
A recent addition to the scheduler is the possibility to add conditions for each of the scheduled tasks.

**Note:** Make sure the native panasonic scheduler (in the controller) is disabled to prevent unexpected behavior of the flow.

### Conditions

Each line in the condition section is a blocking condition. If the condition is met, the scheduled task will be blocked.

---

## Usage: The Dashboard

### Home

This is the home page of the dashboard. Visible is a short overview of the current status of the heat pump. You can enable / disable, see the status and the result of each custom function.

In the column "HEAT" there are a number of custom functions. These functions build on top of each other and you should read them from top to bottom.

1. Starting point is "Shift curve" or "Water temp." value. The [setpoint] for Compensation curve or Direct mode.  
2. When the WAR function is enabled, it replaces the [setpoint] from 1.  
3. When the RTC function is enabled, it corrects the [setpoint] from 2.  
4. When the SoftStart function is enabled, it corrects the [setpoint] from 3.  
5. When the Nightreduction function is enabled, it corrects the [setpoint] from 4. (Note: night reduction will be deprecated soon!)

More details and screenshots of each of the dashboard tabs are present in the collapsed section below.

### Settings

Here are some basic controls of the heat pump. (Not all, because the flow is designed for 1 zone config.

### Charts

#### Temperature

Back to top

#### Energy

Back to top

#### Degree Days

Back to top

### System

In this tab you have multiple sub-sections.

- LOG: See 1000 lines back of all logged events.  
- HARDWARE: Basic readings of the hardware configuration.  
- SENSOR: Select the external or 1wire sensors for custom functions.  
- MQTT: Enable / disable general MQTT block. Basic reading of MQTT messages.  
- MENU CONFIG: Enable / disable parts of the dashboard menu.  
- SYSTEM HEALTH: Extended logging and system information.

Back to top

---

## FAQ

**Q - Can I forward the information coming mqtt messages from the heat pump towards my InfluxDB database?**  
**Details**  
Yes. There is a separate flow available to download. You can find it in the folder "heishamon2influxdb". It requires an additional contrib (node-red-contrib-influxdb). Install the contrib, download the flow, import it, configure the influxdb and your set. You do not need Domoticz or Home Assistant fot that now.

**Q - I use the Node Red Addon in Home Assistant, how to go to the Node Red Gui for editing?**  
**Details**  
Most users should visit via a browser: '`http://Your_NodeRed_IP:1880/ui`'  
In my case this wasn't working, perhaps due to the use of the DuckDNS addon. Use something like ' ' instead.

**Q - Can I use both WAR and RTC at the same time?**  
**Details**  
Yes. If you have both enabled, the WAR function first calculates the SP (Setpoint) depending on outside temperature. Next the RTC function will correct that SP (war) depending on the room temperature. The only SP going to the heat pump will be SP at the end of all the calculations/corrections.

**Q - If I switch off the heatpomp via the Remote Controller will it disable the automation from the Node Red flow also?**  
**Details**  
No, both will work separately. If you turn the heat pump on via the Remote Controller, the pump will switch on. Keep in mind however that if the Node Red flow decides it time to adjust some settings it will act accordingly and overwrite settings.

**Q - I know the function SOFTSTART is experimental, but can you explain what this function does?**  
**Details**  
The idea behind this function is that when the compressor is just started, the frequency of the compressor goes up to 45+Hz. Well out of the efficient range. This is caused by the inner controller of the heat pump. When turned on, it 'wants' to see the impact of the compressor. It looks at the returning water temperature for this. Only when the water temperature returning towards the heat pump is nearing the target temperature, it will start to lower the compressor frequency and get in a stable/efficient mode.  
Throttling... This late throttling behavior can be quiet energy consuming, it can cause the heat pump to generate too much heat at the start and turn off again.  
This SOFTSTART function, when enabled, looks at the moment when the compressor is on, and lower the setpoint to just above the temperature of the returning water. This will in theory cause the heat pump to start throttling down a lot quicker. This function can be useful directly after defrost cycles when the pump starts again, or when the temperature difference between outside/inside is getting smaller.

**Q - How do I add my Entities from Home Assistant like living room temperature?**  
**Details**  
In the Node Red Gui (`http://Your_NodeRed_IP:1880/ui`) you will have to go to the [WP Input] tab;  
In the square "REQUIRED INPUTS FOR FUNCTIONS" you will have to add a node (left pane under Home Assistant) named "Events: state". You can drag and drop this in the square mentioned first.  
It will replace the "TOP33 - panasonic_heat_pump/main/Room_Thermostat_Temp"-node eventually, which you should disable if not using.  
Select the newly created node, then double click to open up the properties window;  
Give is a name of your choosing like 'LivingRoom_temperature'  
In the Entity box you can try to find your sensor entity (assuming you have already setup the MQTT settings earlier).  
Make sure that in the 'Output properties' you have a MSG.PAYLOAD = EVENT STATE  
Check the box 'output on connect' and make sure at the bottom this node is enabled.  
Finally press DONE to close the properties dialog and connect your node to the function node 'set.T_woonkamer_BT'

**Q - How to use a dark theme in the dashboard?**  
**Details**  
In the Node Red Gui (`http://Your_NodeRed_IP:1880/ui`) press the top most right arrow-down sign and select dashboard;  
Now press the Theme-tab and pick your style.

**Q - How to update flow to latest version and keep my inputs, MQTT and Home Assistant settings?**  
**Details**  
Create a personal tab (WP Personal) and place your inputs here (P1, Temperature sensors)  
Give those inputs.sensors each an own [Link Out] node  
Connect those [Link Out] nodes to the already existing [Link In] nodes by double clicking the [Link Out] node and select the corresponding one from the list.  
Some images to explain this:  
Follow the update procedure from the Readme as described here:

Back to top

---

## Release changelog

**Version 25.02 Changes:**  
Fix "Boost DHW now" funciton. Switching to COOL mode when DHW mode is already active.  
Added Energy production for HEAT and DHW bar-chart. Thanks to WP-Rue !!!  
Added BufferTankDelta to the settings page  
Added BufferTank info in SYSTEM > Hardware page  
Improved WP Input tab a lot on connections from external sources. Much clearer

**Version 25.01 Changes:**  
Added "Use Force DHW" toggle on Solar²DHW tab. This can be enabled to solve DHW runs which never end.  
Attempt to fix possible blanc MQTT commands to OperatingMode after BOOST DHW now function.  
Attempt to fix Boost DHW now toggle 'sticking'

**Major changes v25.00:**  
Firmware Support: Added compatibility with Heishamon Firmware 3.9  
SoftStart function rewrite: now with improved relax frequency and TCAP recognition  
Scheduler Enhancements: Added more actions  
Scheduler Enhancements: Added more advanced conditions (room/outside temperature thresholds)  
Sensors: Added extra 1-wire sensor support to show in graphs of DHW, HEAT, and ROOM temps

**SoftStart function:**  
SoftStart Fixes: Resolved bugs related to defrost phase and startup loops

**RTC function:**  
Multiple improvements to prevent premature triggering  
Multiple improvements for the reverting actions

**MQTT Fixes:**  
Eliminated repeating commands like SetZ1CoolRequestTemperature

**Charts & UI Improvements:**  
Home screen: If Fan2 is present, it will show up (and stay) after first value enters.  
Home screen: Added Heater, it will show up (and stay) after first value enters. And when active, it will light up.  
Translated some chart labels from Dutch to English

**Solar²DHW:**  
Forced DHW-only mode during a run for better compatibility with HEAT+DHW  
Improved kWh calculations and graph visuals  
More robust energy tracking in Solar²DHW (fixed NaNs, graph is now more robust, but could increase loading a bit)  
Moved P1 setup to [SYSTEM] > [SENSORS] tab. Much better.

**Miscellaneous Fixes:**  
Reading Panasonic details logic rewritten for fw3.9  
Powerful mode toggle fix  
Pressure readout (TOP115) added

As always, enjoy your heat pump! /
