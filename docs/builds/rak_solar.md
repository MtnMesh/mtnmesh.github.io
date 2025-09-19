# RAK Wireless Solar Build

![RAK Wireless Solar Tree](/static/guides/builds/solar_tree.jpg){ width="50%" }

There are many builds out there for solar Meshtastic nodes, but many require unique modifications and potentially specialized tools. This build is essentially a copy of the build from [The Comms Channel](https://www.youtube.com/watch?v=d2vQ87Th8DI). Highly recommend watching this video if you haven't already. This page offers anecdotal commentary on a duplicate of this build and how it performs.

The benefit of this build is that it is a one-stop-shop solar build with a phillips-head screwdriver being the only required tool for assembly. All of these materials were puchased from [Rokland](https://rokland.com).

By no means are we saying this is the best or cheapest build. However, if you want to click "add all to cart" at one store and have it arrive all in one box, then you might want to give this a try.

## Parts Required:

| Item | Price |
| :-------- | :-------- |
| [RAK Wireless Solar Unify Enclosure](https://store.rokland.com/products/rak-wireless-solar-unify-enclosure-ip67-150x100x45mm-pre-mounted-m8-5-pin-rp-sma-connector-pid-910421?variant=41593246187603) | $69.97 |
| [RAKWireless WisBlock 116016](https://store.rokland.com/products/rak-wireless-wisblock-meshtastic-starter-kit?variant=40074367860819) | $34.97 |
| [RAKWireless Blade LoRa 915 RP-SMA Antenna](https://store.rokland.com/products/blade-antenna?variant=41917927620691) | $12.97 |
| [MakerFocus Flat 3.7V 3000mAh battery](https://store.rokland.com/products/makerfocus-flat-3-7v-3000mah-rechargeable-lithium-polymer-11-1wh-battery-with-jst-type-ph-2-0-plug?variant=41379793207379) | $12.97 |
| [RAKwireless Unify Pole Mounting Horizontal Kit](https://store.rokland.com/products/rakwireless-unify-pole-mounting-horizontal-kit-type-c-910245?variant=41975764090963) | $7.97 |
| [OPTIONAL - RAK Wireless RAK1901 Temp & Humidity Sensor](https://store.rokland.com/products/rak-wireless-rak1901-temperature-and-humidity-sensor-sensirion-shtc3-pid-100001?variant=40510319525971) | $8.97 |
| **---** | **---** |
| **Subtotal (pre-tax)** | $147.82 |

***Note: All prices are as of March, 2025***

## The Build
The build process was pretty painless. There are no instructions on how to assemble the node, but the process is decently straight-forward. Especially if you follow [The Comms Channel](https://www.youtube.com/watch?v=d2vQ87Th8DI) build guide. There are a few things to remember with this build that deviate from the video:

1. This build includes a temperature / humidity sensor to monitor the environment inside of the node's enclosure. This is mainly for overheating issues and detecting water leaks. While this is not _technically_ necessary, we highly recommend it to help keep an eye on the node's health.
2. This parts list above includes a horizontal mounting kit. We used this because we eventually mounted the node to horizontal cross-beam on a tower with a 45-degree tilt to the South for better solar exposure. There are multiple mounting solutions for this hardware, so it'll be up to you as to which version is best. They include:
    - [Horiztonal Pole Hardware](https://store.rokland.com/products/rakwireless-unify-pole-mounting-horizontal-kit-type-c-910245?variant=41975764090963)
    - [Vertical Pole Hardware](https://store.rokland.com/products/rakwireless-unify-pole-mounting-vertical-kit-type-a-910247?pr_prod_strat=e5_desc&pr_rec_id=480f1e3a9&pr_rec_pid=7147991826515&pr_ref_pid=7391192285267&pr_seq=uniform)
    - [Hook Hardware](https://store.rokland.com/products/rakwireless-unify-unify-hook-loop-kit-type-jcool-grey-pid-910231?variant=41904351608915)
3. Dessicant packs. Can't state this enough; unless you want your node to smell funky and grow mold, toss a small dessicant pack / moisture absorber in the enclosure. We purchased them in bulk from [Amazon](https://www.amazon.com/dp/B0CY8HM7HR), but you can find dessicant packs in many moisture-sensative products such as beef jerky or nori (seaweed) at your local grocery store.

## The Final Setup

Here's a look inside of the node with all parts assembled prior to deployment.

![Node Internals](/static/guides/builds/solar_internals.jpg){ width="30% }

And here is the current deployment of the node. As of April 19, 2025, the node has been in the wild for more than 2 weeks. It has been steadily charging during the day with the charge not dropping below 80%.

![Node Deployed](/static/guides/builds/solar_deployed.jpg){ width="30% }