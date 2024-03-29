# Ender-3-Marlin-2.0.7.2-Firmware

*** BLtouch is used as the Z-Axis stop, that means I have removed the z-axis stop switch.

My custom firmware for an Ender 3 v1 using a BigTreeTech Mini SKRv1.2 with a BLtouch v3.1 and stock metal mount.

My compiled firmware.bin is under the folder compiled_fw, I wouldn't just use it, I would compile your own based on what you want and your probe offsets, but you can try at your own risk, its your printer!


The Official readme is official_readme.md or alternatively just go to the Marlin github repository.

This is based off of the official Marlin github repository: https://github.com/MarlinFirmware/Marlin/commit/5ee1087959f88dc60386ff3caa21e75d9e20b128

*** BLtouch is used as the Z-Axis stop

I fumbled around with issues and found this github issue: https://github.com/MarlinFirmware/Marlin/issues/20105. I was having similar issues, using the BTT fork of Marlin.
So I ended up just using the official Marlin branch as that issue seem to resolve after a commit on December 14th. I am using the latest build at the time of this (February 11th, 2021) with this last commit https://github.com/MarlinFirmware/Marlin/commit/5ee1087959f88dc60386ff3caa21e75d9e20b128.



Configured using the following guide:
https://www.reddit.com/r/ender3/comments/hymv70/marlin_20x_guide_skr_mini_e3_v12_ender_3/


- Probe Points are 3 x 3 - firmware3x3.bin and 4x4 - firmware4x4.bin 
- I went ahead and added a s-curve acceleration precompiled firmware - firmware-scurve-4x4.bin and a precompile firmware with scurve and linear advance both disabled
  - These are located in the precompiled firmware folder located in this repository labeled 'compiled_fw'

- ***** Bltouch is used at the Z-Axis stop
  - The mount used is the metal one that comes in the bltouch creality kit: https://img.staticbg.com/images/oaupload/banggood/images/29/4F/302fbeca-2822-4ff5-a3b5-b3c7d0e42d8d.png
  - I found my probe offsets to be NOZZLE_TO_PROBE_OFFSET { -43, -6.5, 0 } to start.
    - I adjusted the z offset usign the z-offset wizard, see video here: https://www.youtube.com/watch?v=fN_ndWvXGBQ
      - If you prefer the old fashioned way see here: https://www.youtube.com/watch?v=Q5M7DvdMcew
        - If using the firmware config I have above you will need to disable the z axis safe setting using this command: M211 S0 (this allows the axis to go below 0.00)
          - renable it with M211 S1
  
- No filament runout sensor

- buzzer is disabled
  - if you want to disable the buzzer your self, the location is in Marlin/pins/stm32f1/pins_BTT_SKR_MINI_E3_common.h/
     - search for #define BEEPER_PIN and set the value to '-1'
    
