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

4.  You should now notice new sensors available in HomeAssistant.
    <br><br />
    
### Sensors Available
- Cumulative Power Usage
- Line 1 Voltage (volts)
- Line 1 Current (amps)
- Line 1 Power (watts)

*Additional sensors only available on 50amp units:*
- Line 2 Voltage (volts)
- Line 2 Current (amps)
- Line 2 Power (watts)
- Total Watts Between Lines ([code for template sensor](total_watts_sensor.yaml))
    <br><br />

### Future Updates
- Addition of a sensor for Error reporting
- Additional sensor that combines L1 and L2 power values to give you a total watts for the unit 
- Support for resetting the cumulative kWh counter via HA
    <br><br />

### Contributions
Many thanks to everybody who helped with this project, regardless of the capacity. Without the help of each and every one of you, this project would not have been sucessful. Extra special thanks goes out to:
- [spbrogan](https://github.com/spbrogan)
- [makifoxgirl](https://github.com/makifoxgirl)
- SergeantBort
