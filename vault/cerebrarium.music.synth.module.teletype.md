---
id: 30fb9719-ad12-4d46-af75-6d357e348a92
title: Teletype
desc: ''
updated: 1611409307860
created: 1609508666974
---
# Monome Teletype

[Official website](https://monome.org/docs/teletype/)

[Repo for software](https://github.com/monome/teletype)

[Repo for hardware](https://github.com/monome/teletype-hardware)

## build log

- purchased panels and pcb on 2020-11-30
- purchased components on 2020-12-19 (digikey)
    1. PLP1-350-F x 8 backordered
    2. AD5687RBRUZ x 2 backordered
- purchased missing components on 2020-12-29 (mouser)
    1. PLP1-350 instead of PLP1-350-F
        - Round lens instead of flat lens
        - All other dimensions are identical and should fit

## notes

**2020-12-31 9:31 PM**
- This build uses 2-56 screws and standoffs (Mcmaster 91780A023, 91772A077, 91772A073) that are kind of hard to find. Had to look for the datasheets for these and order alternatives. Hopefully they will fit.

- Along with the [[Veils panels|cerebrarium.music.synth.module.veils]], the panels for these were scratched. Perpendicular to the aluminum brushing. I suspect poor packaging on the seller's end. It was shoved in a plastic baggy barely big enough to fit both the panels and the pcb with no other protection (just in a box with a dozen more pcbs and panels). I was more frustrated with the poor quality of the Veils panels so I didn't mention these. 

**2021-01-06 11:19 PM**
- Rest of the components that were missing arrived with the veils component order.
- I'm pretty excited for this build. It's pretty much a blank slate module that can do anything I can think of and code.

**2021-01-10 2:53 PM**
- Compiled the IBOM for Teletype with Eagle.
- Sorted and checked all needed components.
- **SW40 and ISP not needed.**

**2021-01-16 4:14 PM**
- Started applying solder paste 

**2021-01-16 4:58 PM**
- Finished applying solder paste
- Started placing 0402 resistors

**2021-01-16 5:52 PM**
- Finished placing all 0402 resistors
- Started placing 0402 capacitors

**2021-01-16 6:34 PM**
- Substituted C27 (100n ceramic capacitor) with a 100n ceramic capacitor with a higher working voltage rating

**2021-01-16 7:08 PM**
- Finished placing all capacitors
- Started placing diodes

**2021-01-16 7:20 PM**
- Finished placing diodes
- Started placing LEDs / etc.

**2021-01-16 7:43 PM**
- Started placing ICs

**2021-01-16 8:13 PM**
- All SMD components placed

**2021-01-16 8:16 PM**
- Start up heat plate. Warm up to 100C
- Placed PCB around 85C mark

**2021-01-16 8:25 PM**
- Crank up to 230C

**2021-01-16 8:35 PM**
- Turned heat plate off.
- Cooling PCB down on the heat plate.

**2021-01-16 8:46 PM**
- Removed PCB from heat plate.
- Cooling down on a cold metal surface.

**2021-01-16 9:38 PM**
- Inspection time
- Bare eyes:
    - I seem to have figured out an optimal amount of solder paste application.
        - Most of the pads have perfect joints.
    - Bridges on tight chips are inevitable with solder paste.
- Microscope
    - Some pads on the edge of the board aren't fully flowed and need touch-up
    ![](/assets/images/2021-01-16-21-43-45.png)
    - Balled up joint. This is a problem with component placement, or the amount of paste on one side of the pad. Usually the component will stand up on it's own if there was too much solder paste on one side though
    ![](/assets/images/2021-01-16-21-49-42.png)
    - Another ball-up. This one is a bit subtle but from the sides I can see that the resistor is slightly lifted on one side. The balled up side actually does not have contact with the pad/solder
    ![](/assets/images/2021-01-16-21-53-40.png)
    - This is an odd one. Solder balled up on the component and not on the pad. This is most likely due to dried up solder paste and slightly lifted component.
    - It's possible that the pad has contact with the component, but I will touch this up just in case
    ![](/assets/images/2021-01-16-22-07-57.png)
    - Rouge ball of solder on each side of the 1206 capacitor.
    - Simply running the iron and dragging it to one side of the pad will fix this.
    - I can see this on every single 1206 package.
    ![](/assets/images/2021-01-16-22-09-13.png)
- Loupé
    - Another check with a loupé as a microscope is limited to a bird's eye view and its resolution

**2021-01-17 12:00 PM**
- Yesterday, after inspection I cleaned up bridges and dry joints.
- Due to the amount of solder paste, I had to wick away some solder from the bridges on the STM32.
    - As a result, I took away a bit too much solder, which resulted in a (potentional) dry joint
    ![](/assets/images/2021-01-17-12-02-42.png)
    - I remedied this by applying a lot of flux, then dragging the iron along the pins to evenly distribute the existing solder to the pins that have dry joints.
        - On some sides there weren't enough left to drag around, so I tinned the iron with the tiniest amount of solder and did the same. with enough flux, this will not bridge the pins.
        - Just the right amount of solder would be left behind on each joint
        ![](/assets/images/2021-01-17-15-15-26.png)
- Soldered all the hardware except the potentiometer and jacks.
- Turns out the DIP socket + pin headers listed in the Bill of Materials for the OLED header lifts the screen a tiny bit too high. There is not enough space between the screen and the panel for the panel to fit.
    - I could substitue them with low profile sockets, but I didn't have it stocked.
    - It would have also worked if I replaced only the male headers, but unfortunately these male headers do not fit in DIP sockets.
    - At this point, my option is to:
        1. Purchase low profile sockets (mouser reference : [517-929984-01-20-RK](https://kr.mouser.com/ProductDetail/3M-Electronic-Solutions-Division/929984-01-20-RK/?qs=%2Fha2pyFaduh65k0%252BENFIKH%2FjmgqQmrFcQW016WE0H3Ua5m7VtlBHQinfFgBmn0lN&utm_source=octopart&utm_medium=aggregator&utm_campaign=517-929984-01-20-RK&utm_content=3M))
        2. Pull out a few pins and hack up my own headers.
    - Safest bet is to go with the low profile sockets. These are the same ones used for the Westlicht Performer.
- Technically, at this point I could power it up and see if it flashes properly. If it doesn't flash properly, I need to work on the STM32 joints again.
- I decided to wait until I get the height of the screen properly before flashing, because having a screen just feels better when the module boots up.

**2021-01-17 3:18 PM**
- I will have to add the proper headers for the screens in my next mouser cart.
- I have the Fade, Kinks, Plaits, Stages left to build, so I'll choose one and order the components with the headers I need.

**2021-01-22 9:56 PM**
- Replacement headers arrived
- Desoldering original

**2021-01-22 10:59 PM**
- Finished desoldering original
- It was a pain in the ass
- Preci-dip 20 pin connectors are a pain in the fucking ass to desolder
- CHECK LEVELS OF ANY OLED SCREEN WITH THE PANELS BEFORE SOLDERING PIN HEADERS
- CHECK LEVELS OF ANY OLED SCREEN WITH THE PANELS BEFORE SOLDERING PIN HEADERS
- CHECK LEVELS OF ANY OLED SCREEN WITH THE PANELS BEFORE SOLDERING PIN HEADERS

**2021-01-23 1:03 AM**
- Tried flashing on a Mac. Did not work.
- Suspected faulty cables (USB-C to A). Was not the case.
- Switched to Windows. Worked first time (USB-A to A).
- Soldered the jacks and potentiometer.
- Realized the screws are too short to reach from the panel to the spacer.
    - Will have to be like this for now until I order another batch of components
- CV 3's LED is always on. but it's too late and I'm tired.

**2021-01-23 10:07 PM**
- Reflowed CV 3's LED and the components that are in series to it.
- It is still always on, but when I connect the USB keyboard to the module, it partially works
    - Unlike other CV LEDs, it's either ON or OFF, it doesn't go from dim to full brightness depending on the voltage
- Chipped a bit of the LED off while touching it up.
- I don't know enough about electronics to troubleshoot this on my own. Nor do I have the energy to do this today, so I will leave it here.

**2021-01-23 10:05 PM**
- With the help of a friend, narrowed it down to a problem where CV output 3 is recieving high voltage.
- When given 1 volts as an output, it was receiving 11.9V, thus making it turn brighter than others.
- Also, the power switch for USB (U1) burned. My first magic smoke!
    - I guess it couldn't handle my keyboard.
- I should order replacement for U1 and a cheap usb keyboard.

**2021-07-04 14:50**
- This is not logged, but I troubleshot some but still have not finished it. It's been a while.
- Eurorack is currently on the backburner, so it may take a bit to get back to this.
