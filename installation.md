<a id="top"></a>
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
- Third; It is advicable to know if you system is setup with the correct time/date. <br>

These will be explained here. <br>

[Back](readme.md)

****

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

[Top](#top) / [Back](readme.md)

****

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
> The Dashboard 1.0 pallette is indeed depricated by Node Red. But I have not migrated to Dashboard 2.0 yet. (=ToDo) Despite that, it still works fine.

[Top](#top) / [Back](readme.md)
 
****

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

[Top](#top) / [Back](readme.md)

****

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
- Find and Double-click **MQTT (x.x.x.x)** <br>
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
