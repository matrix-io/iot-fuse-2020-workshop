# Overview

This workshop will go over how you can easily employ a privacy-focused voice assistant with MATRIX devices, an IoT development platform powered by Arm microcontrollers and Xilinx FPGAs, on the Mozilla IoT WebThings Gateway to quickly deploy an effective voice-enabled product for your home or company.

The workshop will walk through how to use the Mozilla IoT Gateway through its UI as well as with voice commands to read MATRIX device sensors, control LEDs, GPIOs, and more. Participants can then create custom rules with these tools to set up their assistant to suit their needs, from personal home automation, to warehouse item provisioning, or retail voice assistance.

We will show you how to:

- Control the LEDs manually from the Things UI
- Enable the voice assistant (one you can use from a website)
- Trigger LEDs from voice assistant
- Add rule based on UV value to trigger notification & LED color change

# 1. Enabling The MATRIX Addon

The image provided for this workshop contains the Mozilla IoT gateway preinstalled with our MATRIX addon. Once logged into your Gateway, go to **settings** -> **Add-ons** and then click **Enable** on the MATRIX addon.

![](./images/matrix_addon.png)

With the addon enabled, you can now add the MATRIX Creator as a Thing. Go into your **Things** menu and select the **+** icon. Click **Save** and then **Done** on the Creator.

![](./images/add_thing.png)

# 2. Interacting With The MATRIX Creator

Each Thing we add will have a menu we can access to control or view various properties Click on the Creator's node-like icon to access its menu.

![](./images/thing_icon.png)

The menu will contain a live view of the Creator's sensor data and and option to control the LEDs.

![](./images/thing_menu.png)

Feel free to edit the **Color** property and then toggle the **On/Off** switch! The LEDs will change to the colors that you set.

# 3. (TODO) Creating Custom Rules

# 4. (TODO) Enabling The Web Voice Assistant
