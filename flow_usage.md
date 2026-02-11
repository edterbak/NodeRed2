<a id="top"></a>
## Flow Usage

<a id="quick_start"></a>
### Quick start
Here are the minimal things to do / set.

#### Heishamon config
When you start the Node Red flow for the first time, it requires some time to read the data from heishamon. This can take up to 10 minutes, depending on your heishamon setting. My settings are given below. For me they work fine.

| Config item  | Value |
| ------------- | ------------- |
| How often new values are collected from heatpump |	**5 seconds** |
| How often all heatpump values are retransmitted to MQTT broker |	300 | 

#### Test MQTT connection
You can verify the mqtt configuration from within the Node Red dashboard:
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > MQTT** <br>
- Press the **[TEST]** button behind "MQTT Broker"
- Look at the response below it. It should say "Connected" with a recent date/time stamp.

#### Time Zone
To set the correct timezone within Node Red dashboard:
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > SETTINGS** <br>
- Select your time zone<br>
- Press **[Save]**

#### Persistant storage
During the installation of Node Red and the flow, you have enabled persistent storage. To verify this has been done correctly, you need to look at the logs.
- Open the Dashboard http://<host-ip>:1880/ui/ <br>
- Go to tab **SYSTEM > LOG** <br>
- Not long after the flow has started, a log entry should be shown with information about the persistent storage. Check it.<br>
  

[Top](#top) / [Back](readme.md)

*******

<a id="guidelines"></a>
### Setup guidelines
These are the setup guidelines

[Top](#top) / [Back](readme.md)

*******

<a id="functions"></a>
### Functions
There are a number of functions...

[Top](#top) / [Back](readme.md)

*******

<a id="tips"></a>
### Tips
Below are usefull tips.

[Top](#top) / [Back](readme.md)

*******



