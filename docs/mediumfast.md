# Migration to MediumFast

We're flipping our mesh from the default LongFast to MediumFast on October 1, 2025.

[Click here for a configuration link if you don't feel like reading.](https://meshtastic.org/e/#CgcSAQE6AggNCg0SAQEaCExvbmdGYXN0EhQIARAEOAFAA0gBUB5oAcAGAcgGAQ)

!!! warning
    If you have a filter on your node, make sure it's compatible with the new MediumFast frequency before continuing. LongFast (slot 20) operates at `906.875 MHz`. MediumFast (slot 45) operates at `913.125 MHz`.

## Why We're Moving Modem Presets

All Meshtastic devices default to LongFast out of the box. That's a great preset for getting a small mesh off the ground, but once you get more than 60 nodes chatting in an area, you start getting message collisions. More collisions means dropped packets, network congestion and decreased performance. Considering that some node DBs have more than 200 nodes and channel usage above 45%, we're well past that threshold for migration.

The good news is that this isn't uncharted territory by any means. There are several meshes that have already flipped modem presets. Meshtastic also [posted a post on their blog](https://meshtastic.org/blog/why-your-mesh-should-switch-from-longfast/) detailing when and why a mesh should flip presets.

## Migrating Your Node to MediumFast

### Backing Up Your Node Settings

Backing up your node settings before any big changes is always a good idea. Thankfully it's easy to do with the [Meshtastic apps](https://meshtastic.org/docs/software/) or the [Meshtastic CLI](https://meshtastic.org/docs/software/python/cli/). Below is a quick way of backing up your node's settings using the CLI:

```bash
meshtastic -t {NODE_IP_HERE} --export-config > node_settings.yml
```

To restore your settings, run the following command:

```bash
meshtastic -t {NODE_IP_HERE} --configure node_settings.yml
```

!!! note
    One sneaky trick with this configuration YAML is that you can delete specific lines that you don't want copied over. For instance, if you don't want to migrate your channel URL settings, just delete that line from the configuration. Just be careful and always keep a backup of your original config before making any modifications.

### Docker Volumes

If you're using [Meshtasticd via Docker Compose](https://hub.docker.com/r/meshtastic/meshtasticd), you can also map your node's configuration to a separate docker volume. That way you can flip between presets quickly if need be. You just have to uncomment the one you want and recreate the container. For example:

```yaml
services:
  meshtasticd:
    image: meshtastic/meshtasticd:alpha-debian
    container_name: meshtasticd
    devices:
      - "/dev/spidev0.0"
      - "/dev/gpiochip0"
      - "/dev/i2c-1:/dev/i2c-1"
    ports:
      - "4403:4403"
    cap_add:
      - SYS_RAWIO
    volumes:
      - ./config.yaml:/etc/meshtasticd/config.yaml:ro
#      - ./LongFast:/var/lib/meshtasticd # previous modem preset
      - ./MediumFast:/var/lib/meshtasticd # new modem preset
    restart: unless-stopped
```

You still have to configure each of the volumes from scratch, but it's a quick way of flip-flopping between presets if that's your vibe.

### Quick Configure Link

[If you want a quick easy-button configuration, use this URL](https://meshtastic.org/e/#CgcSAQE6AggNCg0SAQEaCExvbmdGYXN0EhQIARAEOAFAA0gBUB5oAcAGAcgGAQ)

This link will set the following settings:

- MediumFast LoRa modem preset with frequency slot of 45

- 3 Hops (feel free to bump this up as you see fit, but please be gentle)

- MediumFast as primary channel (0) with default PSK of `AQ==`

- LongFast as secondary channel (1) with default PSK of `AQ==`

This will NOT change your node's network role (Client, Client_Mute, etc.)

[See our guide on recommended configurations for additional node settings.](/config)

## Setting up a LongFast Bridge Network

It's totally possible to create a network bridge between the 2 modem presets. You can have 2 radios on the same local area network (LAN) or even have a single linux box connected to 2 radios at once. Check out [this blog post](https://kr4ccz.net/posts/meshtastic/bridge/) for an example on how to run 2 meshtasticd interfaces at the same time using a docker network.
