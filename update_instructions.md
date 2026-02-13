## Updating the flow

To update the flow to a newer version, you need to perform the next steps:<br>
1. Create a backup<br>
2. Download the latest flow.json<br>
3. Remove current version<br>
4. Import new version<br>
5. Adjust settings<br>
6. Deploy<br>

The steps will be described in more details below

**************

### 1 - Create a backup
This step is actually only required if you have made modifications to the current flow. <br>

*********

### 2 - Download the latest flow.json
Go to the github page and save the flow.json file to your local drive.

*************

### 3 - Remove current version

#### 3.1 - Remove all tabs
In the Node Red flow-editor, you need to:
- **Select** all flow-tabs which start with [WP ] on the top of the screen
- Press **[DEL]**
- Wait until it is finished

> [!WARNING]
> Do **NOT** remove your personal **[WP Personal]** tab.

> [!TIP]
> - To multi-select specific tabs, use [CTRL] + click
> - To multi-select a row of tabs, use [SHIFT] + click

> [!CAUTION]
> If you select too many tabs and press [DEL], the **browser** might **time-out**.
> In that case, select "Wait for browser" to finish or if that does not work, simply reduce the amount of selected tabs for deletion.


#### 3.2 - Remove dashboard items

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

