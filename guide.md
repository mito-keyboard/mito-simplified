# Wireless split

Hii! Do you not want to get carpal tunnel? Or just think that split keyboard are cool? Then you are in the right place!

In this guide you will be learning how to make a wireless split keyboard

This guide is meant to be an extension to the [hackpad guide](https://hackpad.hackclub.com/guide), so if you are a total beginner to keyboards/electronics read that first, and then come back here :)

In this tutorial we a going to use the same form factor board as in the hackpad tutorial, but with different internals, instead of a rp2040 it has a nrf52840 chip inside, which has wireless capabilities.

## Designing you PCBs

<!-- First we need to install some libraries. We will be installing the same OPL libraries as in the hackpad tutorial, here is he [link](https://hackpad.hackclub.com/guide#pcb_design) for that section. -->

Unlike in the hackpad tutorial, where we use the official seeed footprints, this time we need to install install a custom footprint that I made, because  the pins are on the bottom of the board for the the battery charger functionality, which we will be using to charge the battery.

You can download it from here