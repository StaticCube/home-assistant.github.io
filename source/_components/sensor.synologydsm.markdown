---
layout: page
title: "SynologyDSM Sensor"
description: "Instructions how to integrate the SynologyDSM sensor within Home Assistant."
date: 2016-10-30 23:21
sidebar: true
comments: false
sharing: true
footer: true
logo: synologydsm.png
ha_category: Sensor
ha_release: 0.31.1
ha_iot_class: depends
---


This `SynologyDSM` sensor allows getting various statistics from your Synology NAS. Please note that using this sensor wakes up your synology if in hibernation mode.

To use the SynologyDSM sensor in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yml entry
sensor:
  - platform: synologydsm
    host: <Synology IP>
    port: <Synology Port, Default: 5000>
    username: <Username>
    password: <Password>
    monitored_conditions:
      - cpu_total_load
      - memory_real_usage
      - network_up
      - network_down
      - disk_smart_status
      - disk_temp
      - volume_status
      - volume_size_used
```

Configuration variables:

- **host** (*Required*): The IP address of the Synology NAS to monitor
- **port** (*Optional*): The port number on which the NAS is reachable (defaults to 5000). 
- **username** (*Required*): An user to connect to the Synology NAS (a seperate account is adviced).
- **password** (*Required*): The password of the user to connect to the Synology NAS.
- **volumes** (*Optional*): Array of volumes to monitor (defaults to all volumes).
- **disks** (*Optional*): Array of disks to monitor (defaults to all disks).
- **monitored_conditions** (*Required*): Defines a [template](/topics/templating/) to extract a value from the payload.
  - **cpu_other_load**: Displays unspecified load in percentage
  - **cpu_user_load**: Displays user load in percentage
  - **cpu_system_load**: Displays system load in percentage
  - **cpu_total_load**: Displays combined load in percentage
  - **cpu_1min_load**: Displays maximum load in past minute
  - **cpu_5min_load**: Displays maximum load in past 5 minutes
  - **cpu_15min_load**: Displays maximum load in past 15 minutes
  - **memory_real_usage**: Displays percentage of memory used
  - **memory_size**: Displays total size of memory in MB's
  - **memory_cached**: Displays total size of cache in MB's
  - **memory_available_swap**: Displays total size of available swap in MB's
  - **memory_available_real**: Displays total size of memory used (based on real memory) in MB's
  - **memory_total_swap**: Displays total size of actual memory in MB's
  - **memory_total_real**: Displays total size of real memory in MB's
  - **network_up**: Displays total up speed of network interfaces (combines all interfaces)
  - **network_down**: Displays total down speed of network interfaces (combines all interfaces)
  - **disk_name**: Displays the name of the harddisk (creates a new entry for each disk)
  - **disk_device**: Displays the path of the harddisk (creates a new entry for each disk)
  - **disk_smart_status**: Displays the S.M.A.R.T status of the harddisk (creates a new entry for each disk)
  - **disk_status**: Displays the status of the harddisk (creates a new entry for each disk)
  - **disk_exceed_bad_sector_thr**: Displays true / false to indicate if the harddisk exceeded the maximum bad sector threshold (creates a new entry for each disk)
  - **disk_below_remain_life_thr**: Displays true / false to indicate if the harddisk dropped below the remain life threshold (creates a new entry for each disk)
  - **disk_temp**: Displays the temperature of the harddisk (creates a new entry for each disk, uses the unit_system to display in C or F)
  - **volume_status**: Displays the status of the volume (creates a new entry for each volume)
  - **volume_device_type**: Displays the volume type (RAID, etc) (creates a new entry for each volume)
  - **volume_size_total**: Displays the total size of the volume in GB's (creates a new entry for each volume)
  - **volume_size_used**: Displays the used space on this volume in GB's (creates a new entry for each volume)
  - **volume_percentage_used**: Displays the percentage used for this volume in GB's (creates a new entry for each volume)
  - **volume_disk_temp_avg**: Displays the average temperature of all disks in the volume (creates a new entry for each volume)
  - **volume_disk_temp_max**: Displays the maximum temperature of all disks in the volume (creates a new entry for each volume)
