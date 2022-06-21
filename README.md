# The original UV sunhat and the problem

I am that type of person who burns really, really quickly when I am out in the sun.
I try to remember put on sunscreen, but I do not know when how often I should do that.

When I saw a [a tutorial from Adafruit on how to build a sunscreen reminder hat](https://learn.adafruit.com/sunscreen-reminder-hat?view=all), I knew what my next electronics project for the next summer would be.

## Specs of the original sun hat and the need for change

### The microcontroller
The tutorial recommends using Adafruit's [Flora microcontroller](https://www.adafruit.com/product/659) in the sunhat. Although Flora is great for larger wearables (pieces of clothing or large accessories), I found the size of Flora too big for this hat project. In the original tutorial's photos (e.g. [this one](https://learn.adafruit.com/assets/18327)), the Flora is partly hidden behind the hat's ribbon, but it bothers me that I and everybody else can see it peeking there.

Immediately I was wondering if I'd be able to use another, smaller microcontroller to make this hat. But as it happens, the author of the tutorial must have had a similar thoughts, because she had written "The UV sensor does not work with Gemma or Trinket, so a Flora is required". However, this tutorial was published in 2014, when Adafruit had their [older version (v2) of Gemma](https://www.adafruit.com/product/1222).

I started to research if it was possible to use the [newer version (m0) of Gemma](https://www.adafruit.com/product/3501) to make this hat, because Gemma m0 had many upgrades and is more powerful than Gemma's previous versions.

### The calculation of UV load based on skin type and used SPF
I noticed also, that the tutorial code calculates the need for more sunscreen quite simply - if the sensed/measured UV index above a certain threshold and a certain time limit has been passed, then the hat chimes and it is time to put on sunscreen.

I had noticed earlier that if I put on sunscreen when my friends put on sunscreen, some of us would get burns, but the others wouldn't. So I guessed that the type of a person's skin affects the time they can spend in the sun.

Also, since the whole idea of the reminder hat is to remember to put on sunscreen, and sunscreens have different sun protection factor (SPF), that affects how many times more a person can stay in the sun without burning. Simply put, if I can stay in the sun for 15 minutes without burning, with a sunscreen with SPF 30, this means that I can stay in the sun for 30 * 15min = 450min without burning.

## New code
The modified code can be found in `sunhat_code.ino` file.

The code has the skin type 1 as a default.
The code has a SPF 50 as a default.