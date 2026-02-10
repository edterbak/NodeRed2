<a id="requirements"></a>
## Installation details for Node Red<br/>

1. [Node Red installation](#requirements)
	- [Persistant storage](#persistant_storage)
 	- [Required Node Red libraries/pallets](#node_red_libraries)
  	- [Timezone setup](#time_zone)
2. [Flow installation](#flow)

****

## Node Red installation
There are some things required for the Node Red installation itself. <br>
- First; You want your data and settings to survive a reboot, so persistent storage is a must. <br>
- Second; The flow makes use of some node red libraries (or pallettes). These need to be installed.<br>
- Third; It is advicable to know if you system is setupt with the correct time/date. <br>

These will be explained here. <br>

<a id="persistant_storage"></a>
### Persistant storage
You need to change some settings in settings.js to enabled persistent storage.<br/>
In addition it is a good idea to reduce the frequency of writing to your disk. 

In a (proxmox) docker install, you can find this settings.js file in:
```
/var/lib/docker/volumes/FOLDER/_data
```

On a Raspberry Pi, you can find this settings.js file here:
```
/home/pi/.node-red/settings.js".
```

Look for the **contextStorage:** section.
Modify or put in the text as below:
```
contextStorage: {
	default: "memoryOnly",
	memoryOnly: { module: 'memory' },
	file: { module: 'localfilesystem', config: {flushInterval: '300'}, }
},
```
Reboot Node Red for the changes to be applied.<br/>

> [!IMPORTANT]
> Test and verify if persistent storage is working correctly and see that all settings *stick* after a reboot of Node Red.
> Check if you can find context store "file" within Node Red.

> [!IMPORTANT]
> Please also note that this flow writes to disk every 5 minutes. Storage on sd-card is not advised because of possible high wear levels.

------

<a id="node_red_libraries"></a>
### Required Node Red libraries/pallets
- To make use of the dashboard functionality, you need to install the dashboard library.<br/>
		https://flows.nodered.org/node/node-red-dashboard <br/>
- The scheduler makes use of the moment lib<br/>
		https://flows.nodered.org/node/node-red-contrib-moment <br/>
- node-red-contrib-dashboard-bar-chart-data<br/>
		https://flows.nodered.org/node/node-red-contrib-dashboard-bar-chart-data <br/>
- node-red-node-smooth<br/>
		https://flows.nodered.org/node/node-red-node-smooth<br/>
- node-red-node-ui-table<br/>
		https://flows.nodered.org/node/node-red-node-ui-table

> [!NOTE]
> The Dashboard 1.0 pallette is indeed depricated by Node Red. But I have not migrated to Dashboard 2.0 yet. (=ToDo)
 
------

<a id="time_zone"></a>
### Timezone setup
If you use a linux version, make sure you set your correct timezone. You can do this by running this command from CLI root and go through the setup process.
```
dpkg-reconfigure tzdata
```
You can check if it was successful by executing this command
```
timedatectl 
```
If you are running Node Red from within HomeAssistant, follow the instructions from HomeAssistant on how to do that.

[Back](readme.md)

----------

<a id="flow"></a>
## Flow installation
This part will be about the flow installation.

[Back](readme.md)

---------------

## Flow installation:<br/>
<details>
Dashboard: http://IP:1880/ui	(For HomeAssistant: http://IP:1880/endpoint/ui)
Flows: http://IP:1880/#flow

* []() In NR, click on the hamburger icon (three horizontal stripes) in the top right corner
* []() Select Import
* []() Copy/past the content of the .JSON file from this GIT. (or select a file to upload and select the flow.json file offered here)
* []() Click on Import

Once imported, you need to adjust the settings of the MQTT server. <br/>
1. Add the correct information of your broker
2. Use QOS: 0 (maximum for heishamon).
3. Use MQTT v3.1.1 (maximum for heishamon).
Click on the hamburger icon and then configuration nodes. Find the MQTT broker part, double click it and change to your settings.<br/>
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard3.png?raw=true)<br/>

Important >> After import and correcting the MQTT settings, and you might want to connect custom external sensors.<br/>
By default the native Panasonic sensors will be used. But you can connect your custom sensor.  For this go to the flow page to the tab [WP Input], the section indicated below in purple section.
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/v24.00_flow_external_sensors.png?raw=true)  
You can also connect external signals to the flow in this tab. 

** Note 1: The Panasonic Room Thermostat is not very accurate which might cause bad temperature control. <br/>
** Note 2: The Outside temperature sensor on the Panasonic might be subject to heating up due to direct sunlight. This can also have a negative impact on the functions. Personally I use OpenWeatherMap source for outside temperature, but anything is possible.<br/>

[Back to top](#index)

### Opening the dashboard
You can find the link to the dashboard like this:<br/>
![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard2.png?raw=true) ![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/dashboard1.png?raw=true)

[Back to top](#index)
</details>

<!-- headings -------------------------------->
<a id="howto_personalize_customize"></a>
## How to personalize or customize
<details>
It is advised to create a separate tab for your external sources. Any source available in Node Red can be conditioned and used as a sensor in the functions. If you do this in an 'personal tab', then it is likely easier to update later to newer versions. (no guarantees of course)<br/>

[Back to top](#index)
</details>

