# AutoCharging/DisCharging On Mac 
This repository is used to set up battery level detection on a Mac and automatically turn charging on or off based on the user's settings.

## Tools needed
- *Home smart* App iOS
- *shortcuts* App macOS
- A smart plug connected with Mac charger (IKEA in my case)
- *Automation* App on macOS
- Terminal

## Basic Setup
Integrates Ikea smart with Home smart. In this way, the smart integrations can be directly controlled through shortcuts App, which
is able to simplify our implementation.
### shortcut App
- add new shortcut through "+" on the corner
- search for control home on the right-hand pannel and drag it to the left
- locate the smart plug connected to the Macbook charger and set it to be ON, named as "Turn On Mac Charger"
- similarly, create another shortcut and set it to be OFF, named as "Turn Off Mac Charger"

Now, the steps needed for shortcut are done.

### Automation App

Download the zip file called automation app and unzip to the location desired. Its absolute path should be used later for 
background running.

If you would like to set the charge/discharge limit on your own, please modify the following section:


## Terminal Running
Download the attached .plist file to /Users/YourUserName/Library/LaunchAgents/com.YourUserName.batterymonitor.plist. In this file,
it will call to open the automation app that we've written earlier, check the battery level to see whether it meets the conditions and
make decision whether to plug on/off the charger. This check should run every 5 minutes and runs when the file is running.

To make it run on the background without opening terminal and shortcuts, automation, run the following command:
launchctl load ~/Library/LaunchAgents/com.YourUserName.batterymonitor.plist

If any modifications are done to the plist file or to the Automation Applescript, please unload the .plist file and load again.
The command for unloading is
launchctl unload ~/Library/LaunchAgents/com.YourUserName.batterymonitor.plist.

After running the command, nothing will be printed out on the screen.

## Conclusion
Though the setup above, the battery level of Macbook can be monitored and when it reaches the desired level, its charger 
controlled by smart plug will be turned on or off automatically with app running at the background. This helps to better 
preserve battery life.

Hope this repo helps.

If you have any questions, please let me know via seattis@gmail.com.

