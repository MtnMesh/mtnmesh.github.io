# Meshcore Configuration

In addition to Meshtastic, there is now a growing cohort of Meshcore users in the Mountain Mesh community. While the two protocols cannot communicate with eachother, they both work on the same underlying principles. This page is dedicated to the findings and best practices for running Meshcore nodes from our community members.

## Network Congestion and Regions

Similar to Meshtastic, Meshcore can run into congestion issues. As more users join a network, it becomes more likely it is that message colissions will happen. And with nodes reaching from Atlanta up into West Virginia, we're experiencing more and more of these collisions.

This is where Regions come into play. Instead of Meshtastic's hop counts, Meshcore has the ability to limit messages within specific user-defined regions. This can be as large as an entire country or as small as a county. [Pinztrek on GitHub](https://github.com/pinztrek/mesher) is a Mountain Mesh community member and has documented their experiements with configuring regions for Meshcore repeaters.

Common regions within our community include:
```
- us-southeast
  - us-ga
    - us-ga-nw
    - us-ga-ne
    - us-ga-sw
    - us-ga-se
    - us-ga-atl
```

For more examples and configuration guides, see [piztrek's region congestion guide](https://github.com/pinztrek/mesher/blob/main/docs/regions.md).

## Software Recommendations and Quick Links

 - [OpenHop Repeater](https://github.com/openhop-dev/openhop_repeater)

 - [Mesh Stat](https://meshstat.com/#/home)
