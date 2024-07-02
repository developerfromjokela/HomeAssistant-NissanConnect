# NissanConnect [JAPAN] for Home Assistant

An unofficial integration for interacting with Nissan Connect Japan vehicles. Based on the work of [mitchellrj](https://github.com/mitchellrj), [tobiaswk](https://github.com/Tobiaswk/dartnissanconnect) and [dan-r](https://github.com/dan-r/HomeAssistant-NissanConnect). I have no affiliation with Nissan besides owning one of their cars.

If you find any bugs or would like to request a feature, please open an issue.

## Tested Vehicles
This integration has been tested with the following vehicles:
* Nissan Leaf (2012)
* Any other vehicle that works using app should work

### Only for japan!
The API for NissanConnect app for use in Japan. Underlying authentication method and API paths are different compared to US and EU versions. Japanese app uses username and password for sign-in, vs OAUTH in EU.

## Installation

### HACS
This is the recommended installation method.
1. Add this repository to HACS as a [custom repository](https://hacs.xyz/docs/faq/custom_repositories)
2. Search for and install the NissanConnect Japan addon from HACS
3. Restart Home Assistant

### Manual
1. Download the [latest release](https://github.com/developerfromjokela/HomeAssistant-NissanConnect-JP/releases)
2. Copy the contents of `custom_components` into the `<config directory>/custom_components` directory of your Home Assistant installation
3. Restart Home Assistant


## Setup
From the Home Assistant Integrations page, search for and add the Nissan Connect Japan integration.

## Update Time
Terminology used for this integration:
* Polling - the car is woken up and new status is reported
* Update - data is fetched from Nissan but the car is not woken up

Following the model of leaf2mqtt, this integration can be set to use a different update time when plugged in. When HVAC is turned on the update time drops to once per minute.

To prevent excessive 12v battery drain when plugged in but not charging for extended periods of time, the interval reverts to the standard update interval after 4 consecutive updates show the car as plugged in but not charging.
This logic was added to give the benefit of quicker response times on the charging status binary sensor, which can be especially useful when charging with load-balanced or 'smart' chargers.

## Translations
Translations are provided for the following languages. If you are a native speaker and spot any mistakes, please let me know. Also, if somebody is interested in making a Japanese translation, you're more than welcome.
* English
* French
* Italian
* German

## Entities
This integration exposes the following entities. Please note that entities will only be shown if the functionality is supported by your car.

* Binary Sensors
    * Car Plugged In (EV Only)
    * Car Charging (EV Only)
    * Doors Locked
* Sensors
    * Battery Level
    * Charge Time
    * Internal Temperature
    * External Temperature
    * Range (EV Only)
    * Odometer
    * Daily Distance
    * Daily Trips
    * Daily Efficiency (EV Only)
    * Monthly Distance
    * Monthly Trips
    * Monthly Efficiency (EV Only)
* Climate
* Device Tracker
* Buttons
    * Update Data
    * Flash Lights
    * Honk Horn
    * Start Charge
