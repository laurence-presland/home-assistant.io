---
title: SwitchBot Cloud
description: Instructions on how to set up SwitchBot Devices.
ha_category:
  - Hub
  - Plug
  - Remote
  - Switch
  - Sensor
ha_release: '2023.10'
ha_iot_class: Cloud Polling
ha_codeowners:
  - '@SeraphicRav'
  - '@laurence-presland'
ha_domain: switchbot_cloud
ha_platforms:
  - climate
  - switch
ha_config_flow: true
ha_integration_type: integration
---

The SwitchBot Cloud integration allows you to control SwitchBot [devices](https://www.switch-bot.com/) connected through the SwitchBot hub.

## Prerequisites

In order to use this integration, you will need at least a SwitchBot Hub and a SwitchBot account to get a token and secret key from the SwitchBot mobile app in **Profiles** > **Preferences** > **Developer Options**. If **Developer Options** is not present in preferences, tap the App Version (e.g. 6.24) several times (5~15 times) in succession to open the **Developer Options**.

Please note, device names configured in the SwitchBot app are transferred into Home Assistant.

{% include integrations/config_flow.md %}

## Supported devices

- Plug (Wi-Fi only, only available in Japan)
- Plug Mini, both the original and HomeKit-enabled
- IR appliances exposed through the different hubs:
  - ON/OFF for all appliance types excepted "Others"
  - Air Conditioner
- Sensors (Meter, MeterPlus, Outdoor Meter)

## Important considerations

By default, each individual sensor will poll the SwitchBot Cloud API for a status update every 10 minutes (600 seconds). You can request more frequent updates by lowering the `Scan interval (seconds)` in the initial integration setup.

<div class='note warning'>
The SwitchBot Cloud API limits users to 10,000 requests per day so please be cautious when lowering the scan interval.
</div>

<div class='note warning'>
For IR Appliances, the state is inferred from previous commands in Home Assistant and might not reflect reality if you use other ways to control the device.
</div>
