# Home Assistant: Wibeee Component

This is a custom component developed original for its integration with Circuitor Wibeee (3 Phases)

This concept has been proved on similar devices that are listed below:

| Device        | Model           | Link  |
| ------------- |:-------------:| -----:|
|Circuitor Wibeee| 3 phases | http://wibeee.circutor.com/index_en.html |
|Circuitor Wibeee| 1 phase |  http://wibeee.circutor.com/index_en.html  |
|Mirubee| Unknown models |  https://mirubee.com/es/3-productos |

## ToDo


**Notable breaking change**
>
>We finished the great migration. All built-in platforms are now in their own folder. This means that if you had a custom >component or platform that had the same name as a built-in one, you have to rename it. If you still have platforms in your >custom_components/ directory in the old file format, sensor/my_platform.py , rename it to my_platform/sensor.py . It still >works but it will not be supported in a future release.
>


# How it works

Once the devices are installed and connected to local wireless network, current energy consumption values are exposed in xml format, the URL of the exposed web service is:

http://<wibeee_ip>/en/status.xml

Example XML are listed in hithub repository

# Home Assistant configuration

1.- Copy custom comonent into 
```
<hass_folder>/custom_components/wibeee/sensor.py
```

2.- Add device to home assistant configuration file configuration.yaml

```
- platform: wibeee
  name: "Wibeee"
  host: 192.168.xx.xx
  scan_interval: 5
```

3.- Add new created sensors to groups.yaml (optional)

```
supplies_view:
  view: yes
  name: Supplies
  #icon: mdi:network
  entities:
    - group.wibeee_phase1
    - group.wibeee_phase2
    - group.wibeee_phase3
    - group.wibeee_phase4

....
....


wibeee_phase1:
  name: 'Wibeee Phase 1'
  entities:
    - sensor.wibeee_phase1_active_energy
    - sensor.wibeee_phase1_active_power
    - sensor.wibeee_phase1_apparent_power
    - sensor.wibeee_phase1_capacitive_reactive_energy
    - sensor.wibeee_phase1_capacitive_reactive_power
    - sensor.wibeee_phase1_frequency
    - sensor.wibeee_phase1_inductive_reactive_energy
    - sensor.wibeee_phase1_inductive_reactive_power
    - sensor.wibeee_phase1_irms
    - sensor.wibeee_phase1_power_factor
    - sensor.wibeee_phase1_vrms
wibeee_phase2:
  name: 'Wibeee Phase 2'
  entities:
    - sensor.wibeee_phase2_active_energy
    - sensor.wibeee_phase2_active_power
    - sensor.wibeee_phase2_apparent_power
    - sensor.wibeee_phase2_capacitive_reactive_energy
    - sensor.wibeee_phase2_capacitive_reactive_power
    - sensor.wibeee_phase2_frequency
    - sensor.wibeee_phase2_inductive_reactive_energy
    - sensor.wibeee_phase2_inductive_reactive_power
    - sensor.wibeee_phase2_irms
    - sensor.wibeee_phase2_power_factor
    - sensor.wibeee_phase2_vrms
wibeee_phase3:
  name: 'Wibeee Phase 3'
  entities:
    - sensor.wibeee_phase3_active_energy
    - sensor.wibeee_phase3_active_power
    - sensor.wibeee_phase3_apparent_power
    - sensor.wibeee_phase3_capacitive_reactive_energy
    - sensor.wibeee_phase3_capacitive_reactive_power
    - sensor.wibeee_phase3_frequency
    - sensor.wibeee_phase3_inductive_reactive_energy
    - sensor.wibeee_phase3_inductive_reactive_power
    - sensor.wibeee_phase3_irms
    - sensor.wibeee_phase3_power_factor
    - sensor.wibeee_phase3_vrms
wibeee_phase4:
  name: 'Wibeee Phase 4 = Total'
  entities:
    - sensor.wibeee_phase4_active_energy
    - sensor.wibeee_phase4_active_power
    - sensor.wibeee_phase4_apparent_power
    - sensor.wibeee_phase4_capacitive_reactive_energy
    - sensor.wibeee_phase4_capacitive_reactive_power
    - sensor.wibeee_phase4_frequency
    - sensor.wibeee_phase4_inductive_reactive_energy
    - sensor.wibeee_phase4_inductive_reactive_power
    - sensor.wibeee_phase4_irms
    - sensor.wibeee_phase4_power_factor
    - sensor.wibeee_phase4_vrms
```

# Example View in Home Assistant


![hass_view](https://community-home-assistant-assets.s3.dualstack.us-west-2.amazonaws.com/original/3X/8/4/84825f0d8c1653e37be87c0ed4fa68d4832c8bc0.png "Example View in Home Assistant")



# Useful links

Home Assistant community
https://community.home-assistant.io/t/new-integration-energy-monitoring-device-circutor-wibeee/45276
