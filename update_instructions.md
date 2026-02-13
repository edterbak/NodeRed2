## Updating the flow

To update the flow to a newer version, you need to perform the next steps:<br>
1 - Create a backup
2 - Download the latest flow.json
3 - Remove current version
4 - Import new version
5 - Adjust settings
6 - Deploy

The steps will be described in more details below

**************

### 1 - Create a backup
This step is actually only required if you have made modifications to the current flow. <br>

*********

### 2 - Download the latest flow.json
Go to the github page and save the flow.json file to your local drive.

*************

### 3 - Remove current version

yada
********



First: Create a backup of current version. Select all tabs by holding CTRL. Then in the right menu select Export > Download. <br/><br/>

![](https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/Backup_animation1.gif) <br/>RightMouseClick on the GIF and select open in a new tab to see it full screen.<br/>

[Back](readme.md)

--------

## How to update to a newer version

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

[Back](readme.md)

