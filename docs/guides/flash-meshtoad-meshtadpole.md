# Flashing the MeshToad or MeshTadpole

You can flash the onboard EEPROM on the MeshToad or MeshTadpole to support plug and play operation with meshtasticd 2.6.5+.

When flashing, set the `PRODUCT` string to `MESHTOAD` to enable autoconf, regardless of whethor it is acutally a MeshToad or MeshTadpole.

## Flashing with Ubuntu or Raspbian

First, install git if you haven't already: `sudo apt install git`

Next, clone the two needed repositories:

- `git clone https://github.com/command-tab/ch341eeprom`
- `git clone https://github.com/MtnMesh/ch341eeprom-factory`

Next, build ch341eeprom:

```bash
sudo apt install clang libusb-1.0-0-dev llvm make
cd ch341eeprom
make
```

This will produce a file name `ch341eeprom`.

Next, `cd ../ch341eeprom-factory`

### Now for the key part: flashing the device

Look on the MeshTadpole and you will see two holes just to the right of the USB C port. To be able to flash the device you first need to connect these two together temporarily. A small piece of solid core wire works well for doing so. Once the hole are connected, plug the divice in ensure any similar devices are unplugged so that the flasher doesn't do something undesirable to them (a little paranoia is a healthy thing).

Next, run the bits below noting two things: the serial number and the need for sudo. In testing the command didn't work without sudo but, instead, had unhelpful failure messages.

```bash
# change to something unique that is 8 digits
# and does not start with zero
SERIAL_NUMBER=12345678

sudo python3 ch341_factory.py \
--serial $SERIAL_NUMBER \
--product MESHTOAD \
--major-version 1 \
--minor-version 0 \
--bin ../ch341eeprom/ch341eeprom
```

If all goes well, this will have you

1. confirm the serial number
2. flash the device
3. prompt you to do it again

At the prompt to do it again, hit control c to cancel out.

### Confirm it worked

1. unplug the device
2. remove the piece of wire
3. run `sudo dmesg --follow`
4. plug the device in
5. check the output of dmesg right after you plug it in and you should see the serial number you set in the output.

Now, go forth and have fun!
