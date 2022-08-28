# Hughes Power Watchdog in HomeAssistant via ESPHome

*This project is ongoing, so please check back for updates. We encourage you to submit an issue on this repository if you encounter any issues.*

### Materials Needed

-   NodeMCU ESP32
-   BLE Sniffer
    <br><br />

# Instructions

These instructions will assume that you have the latest version of HomeAssistant and ESPHome installed.

1.  Using a BLE sniffer, determine your device's MAC address. Look for a device named "PMD    ###########". There are plenty of BLE sniffer apps available for free. Make a note of your MAC address.

2.  Add the ESP32 to your ESPHome. Copy the code found [here](hughes_esphome.yaml) to your ESP32 config. Change the "*mac_address:*" to your MAC address found in step 1. Save and install to your ESP32.

3.  While your ESP32 is installing and rebooting, ensure there are no devices connected to your Hughes, including your phone. The Hughes only allows a single device to connect at a time.

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
- Support for resetting the cumulative kWh counter via HA
    <br><br />

### Troubleshooting
Depending on the ESP device that you are using, you may run into installation problems when ESPHome attempts to install the code OTA. A common issue is "Error 104", which typically means the ESP device ran out of memory and cannot complete the installation. This is common after the first installation because the ESP is contiuously receiving data from the Hughes device, which can quickly use up memory while an installation is in progress.
<br><br>
An easy work around for this is to utilize the built-in switch. Before you install updated code, turn off the switch. This will disconnect the ESP from the Hughes. Once disconnected, open your mobile app and connect via the Hughes app to prevent the ESP from connecting during the installation process. Install the new code, then disconnect the app and turn the switch back on. The ESP should reconnect shortly after that.
    <br><br />

### Contributions
Many thanks to everybody who helped with this project, regardless of the capacity. Without the help of each and every one of you, this project would not have been sucessful. Extra special thanks goes out to:
- [spbrogan](https://github.com/spbrogan)
- [makifoxgirl](https://github.com/makifoxgirl)
- SergeantBort
