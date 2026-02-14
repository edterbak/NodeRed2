<a id="top"></a>
## Quick start
Here is a shortlist for things you need to do or check after first deployment.
- Check heishamon config
- Check Persistent storage
- Check MQTT connection
- Set time-zone

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



