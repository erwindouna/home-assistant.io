---
title: Fast.com
description: How to integrate Fast.com within Home Assistant.
ha_category:
  - Sensor
  - System monitor
ha_release: 0.88
ha_iot_class: Cloud Polling
ha_config_flow: true
ha_codeowners:
  - '@rohankapoorcom'
  - '@erwindouna'
ha_domain: fastdotcom
ha_platforms:
  - sensor
ha_integration_type: integration
---

The `fastdotcom` integration uses the [Fast.com](https://fast.com/) web service to measure network bandwidth performance.

<div class='note'>

Currently, the Fast.com integration only supports measuring download bandwidth.
If you want to measure bandwidth metrics other then download such as ping and upload, utilize the [Speedtest.net](/integrations/speedtestdotnet) integration.

</div>

Enabling this integration will automatically create the Fast.com Sensor.

By default, a speed test will be run every hour. The user can manually run a speed test via the `homeassistant.update_entity` service.

{% include integrations/config_flow.md %}

## Polling interval

By default, the integration will do a speed test via Fast.com ever hour. 
If you wish to do at a different interval, you can disable the automatic refresh in the integration's system options (Enable polling for updates) and create your own automation with your desired frequency.

For more detailed steps on how to define a custom interval, follow the procedure below.

### Defining a custom polling interval

{% include common-tasks/define_custom_polling.md %}

## Notes

- When running on Raspberry Pi 3 or older, the maximum speed is limited by its 100 Mbit/s LAN adapter.
- The sensor will return the maximum measured speed during a 15-second test.
- Speed tests consume data depending on your internet speed. Make sure to consider this if your internet connection has limited bandwidth.
