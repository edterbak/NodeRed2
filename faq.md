<a id="faq"></a>
## FAQ



### **Q – Can I forward the information coming mqtt messages from the heat pump towards my InfluxDB database?**
<details>
    Yes. There is a separate flow available to download. You can find it in the folder "heishamon2influxdb". It requires an additional contrib (node-red-contrib-influxdb). Install the contrib, download the flow, import it, configure the influxdb and your set. You do not need Domoticz or Home Assistant fot that now.
</details>

---

### **Q – I use the Node Red App in Home Assistant, how to go to the Node Red Gui for editing?**
<details>
    Visit via a browser: 'http://<Your_NodeRed_IP>:1880/ui'<br/>
</details>

---

### **Q – Can I use both CCC and RTC at the same time?**
<details>
    Yes. If you have both enabled, the CCC function first calculates the setpoint depending on outside temperature. Next the RTC function will correct that CCC-setpoint depending on the room temperature. The only setpoint going to the heat pump will be SP at the end of all the calculations/corrections.
</details>

---

### **Q – If I switch off the heatpomp via the Remote Controller will it disable the Node Red flow too?**
<details>
    No, both will work separately. If you turn the heat pump on/off via the Remote Controller, the pump will just switch on/off.<br/>
    Keep in mind however that when the pump is switched off and a scheduled task in Node Red is triggered, it can just turn on the pump for that.<br/>
    This is important to keep in mind when doing maintenance. 
</details>

---

### **Q – Can you explain what the SoftStart function do?**
<details>
    The idea behind this function is that when the compressor is just started, the frequency of the compressor goes up to 45+Hz. Well out of the efficient range. This is caused by the inner controller of the heat pump. When turned on, it 'wants' to see the impact of the compressor. It looks at the returning water temperature for this. Only when the water temperature returning towards the heat pump is nearing the target temperature, it will start to lower the compressor frequency and get in a stable/efficient mode. Throttling... <br/>
    This late throttling behavior can be quiet energy consuming, it can cause the heat pump to generate too much heat at the start and turn off again. <br/><br/>
    This SOFTSTART function, when enabled, looks at the moment when the compressor is on, and lower the setpoint to just above the temperature of the returning water. This will in theory cause the heat pump to start throttling down a lot quicker. <br/>
    This function can be useful directly after defrost cycles when the pump starts again, or when the temperature difference between outside/inside is getting smaller. 
</details>

---

### **Q – How do I add my Entities from Home Assistant like living room temperature?**
<details>
    In the Node Red Gui (http://Your_NodeRed_IP:1880/ui) you will have to go to the [WP Input] tab;<br/>
    In the square "REQUIRED INPUTS FOR FUNCTIONS" you will have to add a node (left pane under Home Assistant) named "Events: state".<br/>
    You can drag and drop this in the square mentioned first.<br/>
    It will replace the "TOP33 - panasonic_heat_pump/main/Room_Thermostat_Temp"-node eventually, which you should disable if not using.<br/>
    Select the newly created node, then double click to open up the properties window;<br/>
    Give is a name of your choosing like 'LivingRoom_temperature'<br/>
    In the Entity box you can try to find your sensor entity (assuming you have already setup the MQTT settings earlier).<br/>
    Make sure that in the 'Output properties' you have a MSG.PAYLOAD = EVENT STATE<br/>
    Check the box 'output on connect' and make sure at the bottom this node is enabled.<br/>
    Finally press DONE to close the properties dialog and connect your node to the function node 'set.T_woonkamer_BT'<br/>
    <img src="https://github.com/edterbak/NodeRed_Heishamon_control/blob/main/images/External%20sources2.png?raw=true" width=75%> <br/>
</details>

---

### **Q – How to use a dark theme in the dashboard?**
<details>
    In the Node Red Gui (http://Your_NodeRed_IP:1880/ui) press the top most right arrow-down sign and select dashboard;<br/>
    Now press the Theme-tab and pick your style.<br/>
    <img src="https://github.com/edterbak/NodeRed_Heishamon_control/blob/ce92e6c7e48323f48742035acb441fb9d3d76aba/images/ChangeTheme.png?raw=true" width=50%> <br/>
</details>

---

### **Q – How to update flow to latest version and keep my inputs, MQTT and Home Assistant settings?**
<details>
    Create a personal tab (WP Personal) and place your inputs here (P1, Temperature sensors)<br/>
    Give those inputs.sensors each an own [Link Out] node<br/>
    Connect those [Link Out] nodes to the already existing [Link In] nodes by double clicking the [Link Out] node and select the corresponding one from the list.<br/>
    Some images to explain this:<br/>
</details>

---

[Back](readme.md)

