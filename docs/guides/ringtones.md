# Custom Ringtones

There are a few devices out there that support the use of RTTTL ringtones. Two options currently available include:

- [SEEED T1000E](https://muzi.works/products/seeed-t1000e)

- [LilyGo T-Deck](https://lilygo.cc/products/t-deck)

Most any node with a buzzer _should_ support custom ringtone configuration as well, but your mileage may vary.

### A Little Background on RTTTL

[YouTube Breakdown by Anas Kuzechie](https://www.youtube.com/watch?v=lRLc0r5BBko)

[Ring Tone Text Transfer Language (RTTTL)](https://en.wikipedia.org/wiki/Ring_Tone_Text_Transfer_Language) is a configuration protocol that allows you to create musical output with a simple string configuration. The default ringtone for most Meshtastic devices looks like this:

`24:d=32,o=5,b=565:f6,p,f6,4p,p,f6,p,f6,2p,p,b6,p,b6,p,b6,p,b6,p,b,p,b,p,b,p,b,p,b,p,b,p,b,p,b,1p.,2p.,p`

That ringtone has 2 parts: a header and the ringtone notes.

#### Ringtone Header

- `24` - Name/identifier for the ringtone (usually ignored)

- `d=32` - Default note duration (32nd note)

- `o=5` - Default octave (5th octave)

- `b=565` - Beats per minute

#### Ringtone Notes

After the header, you have a list of notes to play. Notes are comma-separated and include 4 parameters:

- duration

- pitch

- octave

- dotted-duration

If we break down the first 6 notes in the default ringtone as an example, you'll see this:

- `f6` - F note in 6th octave (duration defaults to 32nd note)

- `4p` - Pause/rest lasting 1/4 the default duration

- `2p` - Pause/rest lasting 1/2 the default duration

- `1p.` - Pause lasting 1 beat with dot (1.5x duration)

- `b6` - B note in 6th octave

- `b` - B note in default octave (5th)

### Meshtastic Notification Config

To change the ringtone on your device, go to the `External Notification` tab in your node configuration via the app or WebUI. Near the bottom of the page, you should see an entry field titled `Ringtone`. Paste your custom ringtone here.

Be sure to set the `Nag Timeout` to a lower number, otherwise it'll pester you over and over again until you press the button on your device. If you set it to `0`, it will only play the notification once.

### Nokia Composer

Here's a good website that allows you to play with RTTTL strings and have them play back for you in the browser. Plus it has some fun examples baked into the page.

[Nokia Composer](https://eddmann.com/nokia-composer-web/)

### Examples

Legend of Zelda Get Item

`24:d=16,o=5,b=120:g,c6,d6,2g6`

Super Mario Theme (Shortened)

`24:d=4,o=5,b=100:16e6,16e6,32p,8e6,16c6,8e6,8g6,8p,8g`

Mario Coin

`24:d=8,o=6,b=200:b,e7`

Mario Power Up

`powerup:d=16,o=5,b=200:g,a,b,c6,d6,e6,f#6,g6,a6,b6,2c7`

Nokia Ringtone

`24:d=4,o=5,b=180:8e6,8d6,f#,g#,8c#6,8b,d,e,8b,8a,c#,e,2a`

Morse Code CQ

`24:d=16,o=6,b=120:8c,p,c,p,8c,p,c,4p,8c,p,8c,p,c,p,8c,8p`

### Use Cases

One thing that's pretty handy to use the ringtone for is a locator. If you send your node a message containing the bell emoji (🔔), it can trigger the ringtone for as long as you allow the `Nag Timeout`. This is useful for those times when you leave your T1000e in the laundry basket and can't find it (like many of us have done).