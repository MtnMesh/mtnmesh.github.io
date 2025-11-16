# Recommended Configuration Settings

In order to maintain a healthy mesh network, we recommend the following configuration settings for your Meshtastic devices.

These settings are intended to facilitate a stable and reliable mesh network. They are based on the collective experience of the Mountain Mesh community and are subject to change as the mesh grows and evolves.

## Radio configuration

### Device

|                      Option | Recommended Config        | Notes                                                                                                           |
| --------------------------: | :------------------------ | :-------------------------------------------------------------------------------------------------------------- |
|                        Role | `CLIENT` or `CLIENT_MUTE` | See :fontawesome-brands-youtube: [Meshtastic Deployment Scenarios](https://www.youtube.com/watch?v=htjwtnjQkkE) |
| NodeInfo broadcast interval | `10800` (3 hours)         |                                                                                                                 |

### Position

|                      Option | Recommended Config   | Notes                                           |
| --------------------------: | :------------------- | :---------------------------------------------- |
|      Smart position enabled | `True`               |                                                 |
| Position broadcast interval | `3600` (1 hour)      |                                                 |
|         GPS update interval | `900` (15 minutes)   |                                                 |
|              Position flags | Disable unused flags | Fixed nodes should disable almost all of these. |

### LoRa

!!! warning
As of October 1, 2025, Mountain Mesh members flipped their nodes over to the MediumFast modem preset. For more information, see the [MediumFast Migration Page](/mediumfast)

|         Option | Recommended Config | Notes                                                                                            |
| -------------: | :----------------- | :----------------------------------------------------------------------------------------------- |
|   Modem Preset | MEDIUM_FAST        | This is the new fast network                                                                     |
|  ^^Hop limit^^ | `5`                | Please do not set this higher than `6`. :pray:                                                   |
| Frequency Slot | 45                 | This is the default. It equates to 913.125 MHz                                                   |
|    Ignore MQTT | `True`             | This is enabled on most `ROUTER` nodes in our mesh.                                              |
|     OK to MQTT | `True`             | Added in `2.5.0`. Enable to show up on online tools like [info.MtnMe.sh](https://info.mtnme.sh). |


## Module configuration

### Telemetry

Please only enable on solar nodes where health data is useful.

|                              Option | Recommended Config | Notes                                                      |
| ----------------------------------: | :----------------- | :--------------------------------------------------------- |
|      Device metrics update interval | `3600` (1 hour)    | Change to `1800` when testing new nodes.                   |
| Environment metrics update interval | `3600` (1 hour)    |                                                            |
|        Power metrics module enabled | `False`            | This is for I²C power monitors, not onboard battery stats. |

Consider disabling the `Environment metrics` / `Air Quality metrics` modules if you are not using the data.


### Neighbor Info

|                Option | Recommended Config |
| --------------------: | :----------------- |
| Neighbor Info enabled | `False`            |

Neighbor Info's functionality has been greatly limited in newer firmware versions. We recommend disabling it for most deployments.
