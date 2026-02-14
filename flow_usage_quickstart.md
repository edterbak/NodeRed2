<a id="top"></a>
## Quick start
Here is a shortlist for things you <ins>need</ins> to do or check after first deployment.
- Check heishamon config
- Check Persistent storage
- Check MQTT connection
- Set time-zone
- When Heating mode = Compensation Curve

Make sure you do them.

[Back](flow_usage.md)

********

### Heishamon config
When you start the Node Red flow for the first time, it requires some time to read the data from heishamon. This can take up to 10 minutes, depending on your heishamon setting. My settings are given below. For me they work fine.

| Config item  | Value |
| ------------- | ------------- |
| How often new values are collected from heatpump |	**5 seconds** |
| How often all heatpump values are retransmitted to MQTT broker |	300 | 

[Top](#top) / [Back](flow_usage.md)

*******

### Persistent storage
During the installation of Node Red and the flow, you have enabled persistent storage. To verify this has been done correctly, you need to look at the logs.
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > LOG** <br>
- Not long after the flow has started, a log entry should be shown with information about the persistent storage. Check it.<br>

[Top](#top) / [Back](flow_usage.md)

*******

### Test MQTT connection
You can verify the mqtt configuration from within the Node Red dashboard:
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > MQTT** <br>
- Press the **[TEST]** button behind "MQTT Broker"
- Look at the response below it. It should say "Connected" with a recent date/time stamp.

[Top](#top) / [Back](flow_usage.md)

********

### Check MQTT block
Rarely it hapens that the mqtt-block is triggered during first startup. Check to see if it is free.
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > MQTT** <br>
- Check the "Block MQTT" toggle. It should be **off**

> [!Note]
> When for some reasone there is a major issue between the dashboard and the heatpump, you can disable the dashboard by turning the "Block MQTT" toggle **ON**.<br>
> The Node Red flow will be in read-only mode then.<br><br>
> :screwdriver: This "Blockk MQTT" is also usefull when doing maintenance.

[Top](#top) / [Back](flow_usage.md)

*********

### Set time-Zone
You need to set the correct timezone <ins>within</ins> Node Red dashboard:
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > SETTINGS** <br>
- Select your time zone<br>
- Press **[Save]**

[Top](#top) / [Back](flow_usage.md)

*******

### When Heating mode = Compensation Curve
We need to make sure the <ins>Node Red CCC settings</ins> matches the <ins>Panasonic Compensation Curve settings</ins>.<br>
First, you should know what your heating modes is:
- Direct
- Compensation Curve

> [!NOTE]
> If you don't know your current heating mode:<br>
> Look in Heishamon: find TOP76 Heating_Mode<br>
> Look in Node Red dashboard: [SYSTEM] > [HARDWARE] under "Hardware configuration" see Heating mode

#### Compensation Curve
We need to make sure the <ins>Node Red CCC settings</ins> matches the <ins>Panasonic Compensation Curve settings</ins>. <br>
- In the dashboard, select **Home**<br>
- "Valve position" should be in **ROOM** position
- **Disable** the functions: **RTC**, **Night Reduction** and **SoftStart**
- Set the **Shift** to **0** (zero)
- Go to CCC menu
- Now **set** the **temperatures** to match your settings exactly as in Panasonic (cloud or controller)
- Do this for **all zones** in use

> [!IMPORTANT]
> Check and confirm the final target temperature in Node Red is exactly as in Panasonic (cloud or controller)<br>
> Check and confirm the zone 1/2 target temperature in Node Red is exactly as in Panasonic (cloud or controller)<br>
> - On the dashboard **Home** under Heat Pump: **Outlet setpoint** temperature<br>
> - On the dashboard **Home** under HEAT (zone 1 and 2): CCC (..°C) **XX** °C

#### Direct
No further action is required



