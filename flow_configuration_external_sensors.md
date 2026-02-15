<a id="top"></a>
## Configuring external sensors

- [Instructions](#instructions)
- [Part 1: In the flow-editor](#part1)
- [Part 2: In the Dashboard](#part2)
- [P1 Instruction](#p1)
- [Limitations](#limitations)

[Back](flow_configuration.md)

********

<a id="instructions"></a>
### Instructions 
By default, the Panasonic heatpump has a limited amount of sensros you are able to use with it. <br>
But.. :) If you are making use of this Node Red flow, you are able to use **any** sensor you want to use for most of the custom functions.<br>As long as your sensor is available within Node Red.

You can use an external sensor for these functions:
- CCC (Outside temperature)
- RTC (Room temperature - Zone 1 and 2)
- Cool (Room temperature and humidity)
- Solar²DHW (Power import and export - P1)

There are two parts of adding an external sensor.
- Part 1: In the flow-editor
- Part 2: In the Dashboard

[Top](#top) / [Back](flow_configuration.md)

******

<a id="part1"></a>
### Part 1: In the flow-editor
Assuming a sensor is available and reporting in Node Red, here are the steps to connect them to the Node Red flow.
1. Go to your **[WP personal]** tab
2. Drag'n'drop a **link out** node on the canvas
3. Double-click on the link-out node and copy the **Name**
  Example: "link out 123"
<br>
<img src="images/dashboard/flow_configuration_external_sensors_01.png" width=50%> <br>

4. Go to the **[WP Input]** tab
5. Look for the correct grey **link in** node<br>
Double click it to **edit**<br>
**Search** for the {name} you just copied<br>
**Tick the box** in front of it<br>
Click **[Done]** <br>
Click on **[Deploy]** to save your changes<br>

<img src="images/dashboard/flow_configuration_external_sensors_02.png" width=50%><br>

[Top](#top) / [Back](flow_configuration.md)

*********

<a id="part2"></a>
### Part 2: In the Dashboard
> [!IMPORTANT]
> For the sensor name/topic to show up in the drop-down list, it must have been received at least once.

In the dashboard:
1. Go to **[SYSTEM]** > **[SENSORS]**
2. Click on the **drop-down** box for the function
3. **Select** the right topic in the list
4. Confirm it is correct when new values is received

> [!NOTE]
> The value of the sensor is only populated after it has been selected AND when a new value is received.

> [!NOTE]
> If the drop-down list is not populated, click the :wastebasket: (Trashbin-icon) and wait for it to populate.

> [!NOTE]
> For connecting a P1 meter there are additional steps required

[Top](#top) / [Back](flow_configuration.md)

********

<a id="p1"></a>
### P1 instruction
There are many types and brands of P1 meters. Not all of them report values in the same manner. <br>

The known variations are:
- Value in W or kW
- Postive or Negative values for Import or Export
- gross or nett import or export values

To configure this:
- Go to **[SYSTEM]** > **[SENSORS]** > **[P1 SETUP]**

> [!NOTE]
> Import is everything coming INTO your house from the grid (POSITIVE value)<br>
> Export is everything going OUT your house to the grid (NEGATIVE value)<br><br>
> > This is in alignment with what the power supplier puts it on the bill

[Top](#top) / [Back](flow_configuration.md)

********

<a id="limitations"></a>
### Limitations
Sensors can send their value in various formats. 
- payload
- object
- array

Sometimes even a combination is happening. <br>
What is working:
- payload as string/number
- array
- object

What is **not** working:
- payload.object

> [!NOTE]
> In case your sensor input is not working correctly, you need to manually condition the incoming value in your [WP Personal] tab.

[Top](#top) / [Back](flow_configuration.md)

********
