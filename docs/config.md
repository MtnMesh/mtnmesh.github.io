---
status: new
---

# Recommended Configuration Settings


## Radio configuration

=== "Device"

    |                      Option | Recommended Config        | Notes                                                                                                           |
    | --------------------------: | :------------------------ | :-------------------------------------------------------------------------------------------------------------- |
    |                        Role | `CLIENT` or `CLIENT_MUTE` | See :fontawesome-brands-youtube: [Meshtastic Deployment Scenarios](https://www.youtube.com/watch?v=htjwtnjQkkE) |
    | NodeInfo broadcast interval | `10800` (3 hours)         |                                                                                                                 |

=== "Position"

    |                      Option | Recommended Config   | Notes                                          |
    | --------------------------: | :------------------- | :--------------------------------------------- |
    |      Smart position enabled | `True`               |                                                |
    | Position broadcast interval | `3600` (1 hour)      |                                                |
    |         GPS update interval | `1800` (30 minutes)  |                                                |
    |              Position flags | Disable unused flags | Fixed nodes should disable almost all of these |

=== "LoRa"

    |      Option | Recommended Config |
    | ----------: | :----------------- |
    |   Hop limit | `5`                |
    | Ignore MQTT | `True`             |
    |  OK to MQTT | `False`            |

## Module configuration

=== "Telemetry"

    |                              Option | Recommended Config | Notes                                                     |
    | ----------------------------------: | :----------------- | :-------------------------------------------------------- |
    |      Device metrics update interval | `3600` (1 hour)    | Change to `1800` when testing new nodes                   |
    | Environment metrics update interval | `3600` (1 hour)    |                                                           |
    |        Power metrics module enabled | `False`            | This is for I²C power monitors, not onboard battery stats |

    Consider disabling the `Environment metrics` / `Air Quality metrics` modules if you are not using the data.


=== "Neighbor Info"

    |                Option | Recommended Config |
    | --------------------: | :----------------- |
    | Neighbor Info enabled | `True`             |
    |       Update interval | `21600` (6 hours)  |
