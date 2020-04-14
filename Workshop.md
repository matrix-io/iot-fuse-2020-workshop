# Overview

This workshop will go over how you can easily employ a privacy-focused voice assistant with MATRIX devices, an IoT development platform powered by Arm microcontrollers and Xilinx FPGAs, on the Mozilla IoT WebThings Gateway to quickly deploy an effective voice-enabled product for your home or company.

The workshop will walk through how to use the Mozilla IoT Gateway through its UI as well as with voice commands to read MATRIX device sensors, control LEDs, GPIOs, and more. Participants can then create custom rules with these tools to set up their assistant to suit their needs, from personal home automation, to warehouse item provisioning, or retail voice assistance.

We will show you how to:

- Control the LEDs manually from the Things UI
- Create custom rules
- Control LEDs based on sensor readings
- Enable a voice assistant (this workshop utilizes the Voco addon based on the Snips.ai voice assistant)
- Trigger LEDs in response to voice-based actions
- Set up audio notifications based on sensor values

# 1. Enabling The MATRIX Addon

The image provided for this workshop contains the Mozilla IoT gateway preinstalled with our MATRIX addon. Once logged into your Gateway, go to **settings** -> **Add-ons** and then click **Enable** on the MATRIX addon.

![](./images/matrix_addon.png)

With the addon enabled, you can now add the MATRIX Creator as a Thing. Go into your **Things** menu and select the **+** icon. Click **Save** and then **Done** on the Creator.

![](./images/add_thing.png)

# 2. Interacting With The MATRIX Creator

Each Thing we add will have a menu we can access to control or view various properties Click on the Creator's node-like icon to access its menu.

<img src="./images/thing_icon.png" width=150 />

The menu will contain a live view of the Creator's sensor data and and option to control the LEDs.

<img src="./images/thing_menu.png" width=400 />

Feel free to edit the **Color** property and then toggle the **On/Off** switch! The LEDs will change to the colors that you set.

# 3. Creating Custom Rules

Custom rules on the MozillaIoT Gateway provide a great drag-and-drop interface for conditional closed-loop control in your project.

To create a custom rule for your project, navigate to "Rules" on the sidebar.

Click the plus icon in the lower right corner to create a new rule.

In rule creation, the basic logic is: if (A), then (B). Optionally, you can change “if” to “while” and combine multiple inputs for (A), and take action against multiple outputs for (B).

![](/images/make_rule.png)

In this workshop, we will be exploring rule creation through to simple functions.
- *Rule 1*: **If** it is a certain time, **then** change MATRIX Creator LEDs color to blue **and** turn MATRIX Creator LEDs on.
- *Rule 2*:  **If** pitch > 30, **then** change MATRIX Creator LEDs color to purple **and** turn MATRIX Creator LEDs on **and** send a browser notification.

### Rule 1
***If** it is a certain time, **then** change MATRIX Creator LEDs color to blue **and** turn MATRIX Creator LEDs on.*

Drag the clock device into the left side of the page and two instances of the MATRIX Creator device to the right side.

When dragging devices, you'll see the left side is inputs and the right side is outputs.

![](/images/inputs_outputs.png)

Name your rule on the top left corner of your screen. I've named it "Lights on at Dusk".

At this point, you should see part of the if-statement filled out as shown below.

![](/images/rule_1_halfway.png)

Adjust the time in the clock device input to be 5 minutes from the present time. 

If you fulfilled the pre-requisites, your Raspberry Pi should already be configued to your time zone. If it is not, please follow the directions [here](https://github.com/matrix-io/iot-fuse-2020-workshop/blob/master/Prerequisites.md#4-enable-ssh-and-set-time-zone) first.

Select the "Color" property in the dropdown for the top MATRIX Creator device and set the color to blue.

Select the "On" property for the bottom MATRIX Creator device.

Your rule should now be complete and look something like this.

![](/images/rule_1_complete.png)

It should trigger in just a few minutes!

Go back to the "Rules" page and select the plus sign on the bottom right corner once again to create *Rule 2*.

### Rule 2
***If** pitch > 30 degrees, **then** change MATRIX Creator LEDs color to purple **and** turn MATRIX Creator LEDs on **and** send a browser notification.*

Drag a MATRIX Creator device to the left as an input, two instances of MATRIX Creator to the right as output, along with a "Browser Notification" button for output.

![](/images/rule_2_halfway.png)

Name your rule on the top left corner of your screen. I've named it "Pitch Change".

Select the property "Pitch" for the input device. Use the dropdown to change the "<" sign to ">", and change the number to 30.

![](/images/pitch30.png)

On the output side, select the "Color" property in the dropdown for the top MATRIX Creator device and set the color to green.

Select the "On" property for the bottom MATRIX Creator device.

In the browser notification output, type "Pitch over 30" in the *Message* field.

Your rule should now look something like this.

![](/images/rule_2_complete.png)

Select the dropdown by **If** in the top left and change it to **While**. This way the reaction occurs only when the pitch is over 30, otherwise the system will revert to its previous state.

![](/images/if_to_while.png)

Go back to the "Things" page and test your rule by moving your MATRIX Creator until the "Pitch" value goes above 30 degrees and move it until "Pitch" is once again below 30 to see its state change back.

# 4. Enabling & Configuring The Voice Assistant

Go to **Settings** -> **Developer** and then click **Create local authorization**.

![](./images/get_token.png)

Click **Allow** on the next page.

![](./images/request_token.png)

Copy the local token shown on your screen.

![](./images/copy_token.png)

Go to **Settings** -> **Add-ons** and then click **Configure** on the Voco addon.

![](./images/voco_addon.png)

Paste the token into the designated field and click **Apply**.

Once the changes have been applied, the Gateway will take you back to the Addon page. Click **Enable** on the Voco addon.

With the addon enabled, you can now add the Voco Snips voice assistant as a Thing. Go into your **Things** menu and select the **+** icon. Click **Save** and then **Done** on the Snips addon.

![](./images/add_Snips_thing.png)

# 5. Interacting with Voice

On the **Things** page, the Snips addon will show up like below.

![](./images/things_after_snips.png)

If you click into it, the Snips addon has the following properties.

![](./images/Snips_thing.png)

If you have a speaker or headphones, attach it to the Raspberry Pi's audio output jack to hear the audio feedback from Snips.

Play around with some of the properties to get a feel for how the Snips addon works.

The wakeword is *Hey Snips*.

Try something like *Hey Snips, set a timer for 30 seconds*. 

Check the addon's [GitHub page](https://github.com/createcandle/voco) for a full list of available commands.


# 6. Creating Rules with Voice
Go back to the "Rules" tab and create a new rule.

This time you'll see some new additions to your available tools.

![](./images/available_tools_for_rules.png)

We are going to create a simple rule to show you how to connect voice commands to visual feedback/reactions.

Create a rule that turns your MATRIX Creator LEDs pink and turns them on when there is 1 Timer set via Snips voice control.

![](./images/set_LEDs_w_timer.png)

Test it out!

Finally, let's test out the speech notifications.

Create another rule which says **Rolling** when the MATRIX Creator's *Roll* property is greater than 90.

![](./images/rolling_rule.png)

Set the volume to **High** by selecting it for the *Level* property.

![](./images/rolling_speech_noti.png)

Go back to the **Things** page to test out the **Rolling** rule.
