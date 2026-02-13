<a id="top"></a>
<a id="flow"></a>
## Flow installation<br/>
In short, the steps you need to perform are:<br>
1 - Download flow.json file<br>
2 - Import the file<br>
3 - Adjust settings<br>
4 - Deploy<br>

> [!NOTE]
> These steps assumes this is a clean installation / deployment. 
> If you are updating, please follow the [update instructions](update_instructions.md)

### 1 Download
- On the main page you will find the file **"flows.json"**. This file contains all the flows. Look for the latest version.<br>
- **Download** it and save it on your local drive.<br>

### 2 Import the file
Go to your Node Red flow editor. `http://<host-IP>:1880/#flow` (or `http://<host-IP>:1880/endpoint/ui` in HomeAssistant)<br>
- Click the **hamburger icon** (three horizontal stripes) in the top right corner
- Select **Import**
- **Select** the **file** flow.json
- Click on **Import**
- Do **NOT** press [Deploy] yet

### 3 Adjust settings
There are some mandatory settings need to be adjusted. <br>
Additionally there are some optional things to change.<br>

#### 3.1 MQTT `(mandatory)`
The flow is not aware yet of your MQTT broker. You need to adjust the settings of the MQTT configuration node.<br>
- In the upper right corner, click the **hamburger icon** again<br>
- Click **Configuration nodes**<br>
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard3.png?raw=true)<br><br>
You will see a list of configuration nodes appear below it.<br>
<br>
- Find and Double-click MQTT (x.x.x.x)<br>
- Change/correct all settings of this node.
	- Name: Rename x.x.x.x to a name of your own<br>
	- Server: (if not present, add) IP adress of your MQTT brokker<br>
	- Fill in the MQTT broker username and password
	- Port: 1833 (default)<br>
	- Protocol: MQTT v3.1.1 (maximum for heishamon)<br>
 	- QOS: 0 (maximum for heishamon)<br>
	

Click on the hamburger icon and then configuration nodes. Find the MQTT broker part, double click it and change to your settings.<br/>

#### 3.2 Theme `(optional)`
#### 3.3 Menu style `(optional)`

<br><br><br><br>

Dashboard: http://<host-IP>:1880/ui	(For HomeAssistant: http://<host-IP>:1880/endpoint/ui)
NodeFlow ed: http://<host-IP>:1880/#flow


Once imported,

Important >> After import and correcting the MQTT settings, and you might want to connect custom external sensors.<br/>
By default the native Panasonic sensors will be used. But you can connect your custom sensor.  For this go to the flow page to the tab [WP Input], the section indicated below in purple section.
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/v24.00_flow_external_sensors.png?raw=true)  
You can also connect external signals to the flow in this tab. 

** Note 1: The Panasonic Room Thermostat is not very accurate which might cause bad temperature control. <br/>
** Note 2: The Outside temperature sensor on the Panasonic might be subject to heating up due to direct sunlight. This can also have a negative impact on the functions. Personally I use OpenWeatherMap source for outside temperature, but anything is possible.<br/>

[Top](#top) / [Back](readme.md)

*********

### Opening the dashboard
You can find the link to the dashboard like this:<br/>
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard2.png?raw=true) ![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard1.png?raw=true)

[Top](#top) / [Back](readme.md)

********

<a id="howto_personalize_customize"></a>
## How to personalize or customize

It is advised to create a separate tab for your external sources. Any source available in Node Red can be conditioned and used as a sensor in the functions. If you do this in an 'personal tab', then it is likely easier to update later to newer versions. (no guarantees of course)<br/>

[Top](#top) / [Back](readme.md)

******
