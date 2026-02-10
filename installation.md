<a id="requirements"></a>
## Requirements for Node Red<br/>

1. [Requirements for Node Red](#requirements)
	- [Persistant storage](#persistant_storage)
 	- [Required Node Red libraries/pallets](#node_red_libraries)
  	- [Timezone setup](#time_zone)

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
