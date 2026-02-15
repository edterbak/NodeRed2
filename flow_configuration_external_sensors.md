## Configuring external sensors

By default, the Panasonic heatpuump limits the amount of sensros you are able to use. <br>
But.. If you are making use of this Node Red flow, you are free to use any sensor you want to use. As long as your sensor is available within Node Red.

All is depending on how your sensor is reporting its values. The most common and easy to use options are:
- MQTT<br>
  Example: Sensors connected via Zigbee2MQTT, ZWave2MQTT or Shelly's with MQTT enabled
- Home Assistant
- Direct via Node Red.<br>
  Sometimes your sensor has a dedicated Node Red pallette available as well. It is worth checking this. 

Assuming a sensor is available and reporting in Node Red, here are the steps to connect them to the Node Red flow.


*Home dashboard*<br>
<img src="images/dashboard/flow_configuration_external_sensors_01.png" width=80%>
<br>

*Home dashboard*<br>
<img src="images/dashboard/flow_configuration_external_sensors_02.png" width=80%>
<br>


