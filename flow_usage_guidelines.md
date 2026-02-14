
<a id="top"></a>
## Setup guidelines
These are the setup guidelines. Please read them carefully and try to understand and follow them.

******

### Rule 1: Start with all functions disabled
If you have just installed this flow for the first time, it is likely you are used to a very simple control. You might have already figured out an operating window which gives you comfort in your home. 

So, please start with that. 

Why? You need to:<br>
- make sure the very basics are working as expected
- build a feel and insights on the 'default' operation

Only after you have confidence the dashboard is working correctly, continue with the next steps.

******

### Rule 2: Enable functions in the right order
There is only **one** correct order of configuring functions. If you do not follow this order, you can expect discomfort.<br>
The basic order is `top-down`. From big imact to little impact.

#### 1 - CCC (Custom Compensation Curve)<br>
This function has the most impact.<br>
Set it up so the temperature of your house is stable and comfortable during the whole day.<br>
> [!IMPORTANT]
> Test CCC, with <ins>all other functions disabled</ins>.<br>
   
> [!NOTE]
> If you are operating your pump with the Panasonic `Compensation Curve`-mode, the Node Red CCC function is always disabled.<br>BUT... Even then. The same rule applies here.
Make sure you have setup it up correctly.

Once this is done, you can continue with the next function.

#### 2 - RTC (Room Temperature Correction)
This function is meant for fine-tuning. In case the room temperature fluctuates due to external influences, the RTC function can compensate a little.<br>
Do not set this function to be too agressive in corrections, as it is meant for fine-tuning. It is not meant to take over the role of the CCC function. 

#### 3 - Night reduction
This function is not for everyone. <br>
There are some users who wish to lower the target temperature of the house during the night.
> [!NOTE]
> Think carefully if you wish to use this functionality. A heatpump opperates more efficiently when kept at stable operating conditions. In theory, the Night reduction function works against this.

#### 4 - SoftStart


1. Scheduler

******

### Rule 3: Enable functions one-by-one
Do not just enable all functions after first start and assume it works. You need to configure each function and verify it is working according to your expectation.<br>
Once configured correctly, wait and look at the result for a couple of days. 

Only after you have verified the function is working correctly and as desired, continue with the next. 

******

### Rule 4: If you think a function is behaving badly, disable the function
Sometimes it appears as if a function is not working as designed. Very easily it is concluded the function is at fault. <br>
First verify it is the function that is at fault by disabling the function.

> Example:
> If you think you have too short compressor-runs and suspect the SoftStart function is at fault, disable it and see what the behaviour is without it.

******

### The custom functions
There are a number of custom functions in the dashboard. Some of these functions work independantly of another function, while other functions build ontop of eachother.

[Top](#top) / [Back](readme.md)

*******
