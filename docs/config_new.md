# Recommended Configuration Settings

To maintain a healthy mesh network, we recommend the following configuration settings based on your node's purpose. These settings prioritize network stability by reducing unnecessary "chattiness" on our shared 3kbps bandwidth (under MediumFast).

!!! info
    These settings are based on the collective experience of the Mountain Mesh community. Settings are subject to change as the mesh grows.

## 📱 1. Personal Mobile Nodes

*For handhelds, vehicle-mounted units, and typical end-user devices.*

Most users should use these settings for their everyday carry (EDC) nodes.

### Radio & LoRa

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Device Role** | `CLIENT` or `CLIENT_MUTE` | Use `CLIENT_MUTE` unless you have a specific need to retransmit. | 
| **Modem Preset** | `MEDIUM_FAST` | Updated Oct 1, 2025. This is the new standard in N.GA. | 
| **Frequency Slot** | `45` | Mediumfast Default (913.125 MHz). | 
| **NodeInfo Interval** | `10800` (3 hours) | | 
| **Hop Limit** | `5` | Please do not set this higher than `6`. 🙏 | 
| **Ignore MQTT** | `True` | Prevents misconfigured nodes from spamming you. | 
| **OK to MQTT** | `True` | Allows you to see your node on [view.MtnMe.sh](https://view.mtnme.sh). | 

### Position & Telemetry

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Smart Position** | `True` | Updates more frequently while you are moving. | 
| **Broadcast Interval** | `3600` (1 hour) | Base interval when stationary. | 
| **Fixed Position** | `False` | Mobile nodes should use GPS/Phone location. | 
| **Device Metrics** | `Disabled` | Others on the mesh don't need to know your battery level. | 
| **Env. Metrics** | `Disabled` | Not useful for mobile nodes. | 

---

## 🏠 2. Personal/Local Infrastructure

*For home base stations, attic nodes, backyard masts, and medium-height regional solar deployments.*

As these nodes are stationary and always online, they don't need to be "chatty" about their location or status.

### Radio & LoRa

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Device Role** | `CLIENT` or `CLIENT_BASE` | `CLIENT_BASE` helps ensure your EDC node messages get out. | 
| **Is Un-Messagable** | `True` | Set on non-monitored nodes to prevents users from sending DMs and getting frustrated. | 
| **Modem Preset** | `MEDIUM_FAST` | Updated Oct 1, 2025. This is the new standard in N.GA. | 
| **Frequency Slot** | `45` | Mediumfast Default (913.125 MHz). | 
| **NodeInfo Interval** | `21600` (6 hours) | Stationary nodes don't change info frequently. | 
| **Hop Limit** | `3` | High hop count isn’t useful as not typically a messaged node | 
| **Ignore MQTT** | `True` | Protects the mesh from internet flooding. | 
| **OK to MQTT** | `True` | Allows monitoring the node from the MtnMesh web tools and helps with mesh coordination | 

### Position & Telemetry

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Smart Position** | `False` | These aren’t moving, not needed. | 
| **Broadcast Interval** | `21600` (6 hours) | It’s stationary; no need to reminded people that every hour. | 
| **Fixed Position** | `True` | Manually set coordinates in the app if no hardware GPS. | 
| **Device Metrics** | `10800` (3 hours) | Only for solar nodes, otherwise disable. | 
| **Env. Metrics** | `10800` (3 hours) | Only if equipped; Used to checking for enclosure leaks or overheating, otherwise disable. | 

---

## 🏔️ 3. Coordinated Public Infrastructure

*For high-sites moving messages across the state. These are generally ham towers on actual mountains.*

**Note:** Only coordinated infrastructure nodes should use the `ROUTER` role. Improperly configured routers can cause network-wide degradation. Please join the Discord to discuss your site before using these settings.

### Radio & LoRa

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Device Role** | `ROUTER_LATE` | Better for mesh health 95% of the time than `ROUTER`. | 
| **Modem Preset** | `MEDIUM_FAST` | Updated Oct 1, 2025. This is the new standard in N.GA. | 
| **Frequency Slot** | `45` | Mediumfast Default (913.125 MHz). | 
| **NodeInfo Interval** | `21600` (6 hours) | High-sites are constant; minimal updates needed. | 
| **Rebroadcast Mode** | `CORE_PORTNUMS_ONLY` | Filters out non-essential traffic (e.g., ATAK and range test). | 
| **Hop Limit** | `3` | Prevents telemetry from propagating further than useful | 
| **Ignore MQTT** | `True` | **Crucial:** Protects the mesh from internet flooding. | 
| **OK to MQTT** | `True` | Allows monitoring the node from the MtnMesh web tools and helps with mesh coordination. | 

### Position & Telemetry

| **Option** | **Recommended Config** | **Notes** | 
| :--- | :--- | :--- | 
| **Smart Position** | `False` | Stationary high-site. | 
| **Broadcast Interval** | `21600` (6 hours) | Stationary; updates every 6 hours is plenty. | 
| **Fixed Position** | `True` | Manually set coordinates in the app if no hardware GPS. | 
| **Device Metrics** | `10800` (3 hours) | Monitoring solar and mesh health. | 
| **Env. Metrics** | `10800` (3 hours) | Only if equipped; Used to checking for enclosure leaks or overheating, otherwise disable. | 

---

## Why these settings matter?

The Meshtastic network operates on a shared channel with roughly **3kbps** of usable bandwidth under MediumFast. "Chatty" nodes—those sending updates more than necessary—can quickly saturate the network, preventing actual messages from getting through. By increasing intervals and limiting hops, we ensure the mesh remains usable for everyone.
