<a id="top"></a>

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
	- [Node Red](installation.md#node-red-installation)
		- [Persistant storage](installation.md#persistant-storage)
 		- [Required Node Red libraries/pallets](installation.md#required-node-red-librariespallets)
  		- [Timezone setup](installation.md#timezone-setup)
    - [Flow](installation.md#flow)
- [Flow usage](flow_usage.md)
  - [Quick start](#quick_start)
  - [Setup Guidelines](#guidelines)
  - [Tips](#tips)
- [Update instructions](#updating)
- [FAQ](faq.md)
- [Acknowledgments](acknowledgements.md)
- [Donations](donations.md)  

********

## Abstract
This repository holds a **Node Red flow** which gives you a user friendly dashboard for local control of your Panasonic heatpump.<br>

********

<a id="introduction"></a>
## Introduction
You can connect your Panasonic heatpump to the default CZ-TAW1 module. Then you are locked in the Panasonic ecosystem depending on using the wallmounted controller or Aquarea Smart Cloud.

Alternatively you can connect and control your Panasonic heatpump locally with Heishamon. The heishamon board is created by Egyras. AWESOME job! Get one here: https://www.tindie.com/stores/thehognl/ <br/>
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

********

## What can this Node Red flow do for you (simple benefits)
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
[Back to top](#top)

********
