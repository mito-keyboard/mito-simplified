# Wireless split

Hii! Do you not want to get carpal tunnel? Or just think that split keyboard are cool? Then you are in the right place!

In this guide you will be learning how to make a wireless split keyboard

This guide is meant to be an extension to the [hackpad guide](https://hackpad.hackclub.com/guide), so if you are a total beginner to keyboards/electronics read that first, and then come back here :)

In this tutorial we a going to use the same form factor board as in the hackpad tutorial, but with different internals, instead of a rp2040 it has a nrf52840 chip inside, which has wireless capabilities.

## Installing Libraries

After you created the kicad project, we need to install some libraries. We will be installing the same OPL libraries as in the hackpad tutorial, here is the [link](https://hackpad.hackclub.com/guide#pcb_design) for that section.

Unlike in the hackpad tutorial, where we use the official seeed footprints, this time we need to install install a custom footprint based on the official ones, because the battery charging pins are on the bottom of the board, which we will be using to charge the battery, that are not accessible if we use the official footprints.

You can download it from [github](https://github.com/mito-keyboard/mito-simplified/blob/main/modified-XIAO-nRF52840-SMD.kicad_mod), move it into you KiCad project folder, and add it like a the opl library.

We also need to download the library for the switches, we will be using [marbastlib](https://github.com/ebastler/marbastlib), you can find the installation instructions in the repo

## Schematic

Now we can start creating our schematic.

### Sheets

Because we are creating a split, we esantilay want to have to same circuit for both sides, but not the same layout. We can achieve this by using hierarchical sheets. This way the circuitry we make will be duplicated

To create a hierarchical sheet click on this on the right sidebar or press <kbd>S</kbd>

![image of sheets icon](https://hc-cdn.hel1.your-objectstorage.com/s/v3/efaa0a56ce293a919388c76a0a62ff41d1e1388d_screenshot_from_2025-09-18_17-05-12.png)

Now draw a rectangle and left click, a popup should appear:

![image of popup](https://hc-cdn.hel1.your-objectstorage.com/s/v3/3f98026538ad029f426aab7c6060405b8318c13b_image.png)

Change the `Sheetname` to `left`, and the `Sheetfile` to `side.kicad_sch`, and click ok

Now create another sheet, set `Sheetfile` to `side.kicad_sch`, but the `Sheetname` to `right`.

Your root sheet look something like this:

![image of root sheet](https://hc-cdn.hel1.your-objectstorage.com/s/v3/232d7595f84c8177ca4b1d17ed85b5323bd76470_image.png)

And your left side bar something like this:

![image of left side bar](https://hc-cdn.hel1.your-objectstorage.com/s/v3/9f867ffd0ee5d93b4bf2c06b2958c7e39a89a9f4_image.png)

You can now double click on one of the sheet rectangle in the root sheet, or in the left side bar. You can now place down a switch for example, and navigate to the other sub/child sheet, you will notice that the switch that you placed down in the other sub sheet, is also in this sub sheet.

![left sheet](https://hc-cdn.hel1.your-objectstorage.com/s/v3/af42ed0710e41f69f9a204e6d65187a265a18988_image.png)
![right sheet](https://hc-cdn.hel1.your-objectstorage.com/s/v3/063c21ddabb9d0133596868089eef84a38a7c34a_image.png)

## Circuitry

Now finally we can start to design our keyboard!!!

Add the `XIAO-nRF52840-SMD` symbol:

![symbol add xiao](https://hc-cdn.hel1.your-objectstorage.com/s/v3/9f32be16de764ec09f8353341732586cadcf3e31_image.png)

a switch `SW_Push`:
![symbol add switch](https://hc-cdn.hel1.your-objectstorage.com/s/v3/508824b27185819cc122c0095860bb55e2b5bc6a_image.png)

and a diode `D` (you will see later why we need this):
![symbol add diode](https://hc-cdn.hel1.your-objectstorage.com/s/v3/bfb718542115ac52a37f3bf214ca7d14b19877ea_image.png)

### Keyboard Matrix

You mayu