<img src="https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/banners/top_banner.png" width="1000">
<span style="display:inline-block; margin-right:6px;">
  <a href="https://www.paypal.com/donate?business=ed_terbak%40hotmail.com&no_recurring=0&item_name=Support+my+work&currency_code=EUR">
    <img alt="Donate with PayPal" src="https://img.shields.io/badge/Donate-PayPal-0070ba?style=for-the-badge&logo=paypal&logoColor=white">
  </a>
</span>
<span style="display:inline-block;">
  <a href="https://ko-fi.com/edterbak">
    <img alt="Buy me a Ko‑fi" src="https://img.shields.io/badge/Buy%20me%20a-Ko%E2%80%91fi-FF5E5B?style=for-the-badge&logo=ko-fi&logoColor=white">
  </a>
</span>

********

**Current version:** v26.2.1 Stable<br>
**Release date:** 2026-02-10


********

<a id="index"></a>
## Table of Content
- [Introduction](#introduction)
- [Requirements](requirements.md)
- [Installation](installation.md)
- [Starting for the First time](#first_start)
  - [Starting procedure](#starting_procedure)
  - [Guidelines and tips](#guidelines_and_tips)
    - [How to personalize or customize](#howto_personalize_customize)  
- [Updating instructions](#updating)
- [FAQ](faq.md)
- [Acknowledgments](acknowledgments.md)
- [Donations](donations.md)  

********

<!-- headings -------------------------------->

## Abstract
This repository holds a **Node Red flow** which gives you a user friendly dashboard for local control of your Panasonic heatpump via heishamon. <br>

<a id="introduction"></a>
## Introduction
You can connect your Panasonic heatpump to the default CZ-TAW1 module. Then you are locked in the Panasonic ecosystem depending on using the wallmounted controller or Aquarea Smart Cloud.

Alternatively you can connect and control your Panasonic heatpump locally with Heishamon. The heishamon board is created by Egyras. AWESOME job! <br/>
You can get one from here: https://www.tindie.com/stores/thehognl/ <br/>
```mermaid
---
config:
  look: handDrawn
  theme: forest
---
flowchart LR
    A((A
		Panasonic    
		Heatpump)) <---> B(B
		Heishamon)
	B <---> C{{C
		MQTT Broker}}
    C <---> D(D
		Node Red)
	style D fill:#f9f,stroke:#333,stroke-width:4px
```
* []() A > B: The Panasonic heatpump communicates with the heishamon board
* []() B > C: Heishamon communicates with your MQTT broker
* []() C > D: Node Red communicates with the MQTT brokker

I have chosen to use **Node Red** (=NR) as FrontEnd and automation platform. 
In this repository you will find out all about this Node Red flow.

### What can this Node Red flow do for you (simple benefits)
So, what can it do.
* Offers **local control**. No dependancy on Panasonic Claud at all.
* It provides a nice **dashboard**.
* Shows detailed **graphs and charts** with real‑time or historical data.
* Allows advanced **custom functions** such as CCC, RTC, SoftStart, and Solar‑driven DHW optimizations.
* Works with **any sensor** for the custom functions. 
* **Automations** using schedules with conditions.

### Dashboard impression
Here are just a few images to show the dashboard. For more images look >> here <<

*Home dashboard*<br>
<img src="images/dashboard/home_01.png" width=50%>
<br>

*RoomTemperatureCorrection function*<br>
<img src="images/dashboard/function_rtc_01.png" width=50%>
<br><br>



[Back to top](#index)

********
<a id="installation"></a>
<img src="images/banners/install.png" width="500">

<!-- headings -------------------------------->


<!-- headings -------------------------------->
<a id="howtoinstallnr"></a>


********

<img src="https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/banners/Updating.png" width="500">

<!-- headings -------------------------------->
<a id="howto_backup"></a>
## How to create a backup of your current flow
<details>
There is no easy solution currently know by me to update only changed nodes or flows. <br/>
First: Create a backup of current version. Select all tabs by holding CTRL. Then in the right menu select Export > Download. <br/><br/>

![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/Backup_animation1.gif) <br/>RightMouseClick on the GIF and select open in a new tab to see it full screen.<br/>
[Back to top](#index)
</details>

<!-- headings -------------------------------->
<a id="howto_update"></a>

## How to update to a newer version
<details>	
Update to newer version:<br/>	
I found it is easiest to:<br/> 
1, remove the tabs, WP MQTT, WP Dash, WP Control, WP Solar, WP Scheduler completely<br/> 
2, remove all ui_base, ui_group and ui_tab references from the flows.<br/> 
	*Keep the MQTT (x.x.x.x) and Home Assistant references.<br/>
3, import new version<br/> 
4, correct setup, eg. MQTT server.<br/> 
5, re-connect your personalization’s.<br/> 
	*Not nessesary if you used a WP_Personal tab (see FAQ.md).<br/>
If there are better ideas about this, please inform me. <br/> <br/>

![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/Update_animation_final.gif) <br/>RightMouseClick on the GIF and select open in a new tab to see it full screen.<br/>
[Back to top](#index)	
</details>

********
<img src="https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/banners/dashboard.png" width="500">
<!-- headings -------------------------------->
<a id="dashboard"></a>


[Back to top](#index)
<p align="right">(<a href="#top">back to top</a>)</p>
