# Hughes Power Watchdog in HomeAssistant via ESPHome

*** *I am no longer able to maintain this project as of August 2023. I no longer own an RV or a Hughes device required to coninue work.* ***

### Materials Needed
-   Hughes Power Watchdog Surge Protector *(any PWD or PWS model w/ bluetooth)*
-   NodeMCU ESP32
-   BLE Sniffer/BLE Sniffing App/HomeAssistant BLE Integration
-   HomeAssistant w/ ESPHome add-on
    <br><br />

# Instructions

These instructions will assume that you have the latest version of HomeAssistant and the ESPHome add-on installed.

1.  Using a BLE sniffer device or BLE sniffing smartphone app (Android only), determine your Watchdog's MAC address. Start by looking for a device named "PMD    ###########". Some newer devices may show as "PWS" instead of "PMD". Make a note of your MAC address, as you will need this later.<br><br>It's important to note that Apple devices won't be useful in this step, since Apple purposly obfuscates MAC address data for security purposes. A workaround for this is to use the Bluetoothe LE Tracker integration inside of HomeAssistant if your device has a bluetooth receiver. Once enabled, navigate to your "known_devices.yaml" file, and you will find the PWD/PWS device along with it's associated MAC address.

2.  Add the ESP32 to your ESPHome. Copy the code found [here](hughes_esphome.yaml) to your ESP32 config. Change the "*mac_address:*" to your MAC address found in step 1. Save and install to your ESP32.

3.  While your ESP32 is installing and rebooting, ensure there are no devices connected to your Hughes, including your phone. The Hughes PWD only allows a single device to connect at a time.

4.  You should now notice new sensors available in HomeAssistant. Along with the new sensors, there is a switch built-in to the integration to allow you to stop monitoring via your ESP32 in case you want to connect another device (such as the Hughes app).
    <br><br />
    
### Sensors Available
- Cumulative Power Usage
- Line 1 Voltage (volts)
- Line 1 Current (amps)
- Line 1 Power (watts)
- Error Code Number
- Error Code Description

*Additional sensors only available on 50amp units:*
- Line 2 Voltage (volts)
- Line 2 Current (amps)
- Line 2 Power (watts)
- Total Combined Power (L1 + L2) (watts)
    <br><br />

### Future Updates
- Support for resetting the app's cumulative kWh counter via HA
    <br><br />

### Troubleshooting
Depending on the ESP device that you are using, you may run into installation problems when ESPHome attempts to install the code OTA. A common issue is "Error 104", which typically means the ESP device ran out of memory and cannot complete the installation. This is common after the first installation because the ESP automatically connect to the PWD and is contiuously receiving data from the device, which can quickly use up memory while an installation is in progress.
<br><br>
An easy work around for this is to utilize the virtual switch built-in to the code, available via the HomeAssistant frontend. Before you install updated code, turn this switch to Off. This will disconnect the ESP from the Hughes. Once disconnected, open your mobile app and connect via the Hughes app to prevent the ESP from automatically re-connecting during the installation process. Install the new code, then disconnect the app and turn the switch back on. The ESP should reconnect shortly after that.
<br><br />

### Contributions
Many thanks to everybody who helped with this project. Without the help of each and every one of them, this project would not have been sucessful. Extra special thanks goes out to:
- [spbrogan](https://github.com/spbrogan)
- [makifoxgirl](https://github.com/makifoxgirl)
- SergeantBort
