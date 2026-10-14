# Robbie

![Project Status: Archived](https://img.shields.io/badge/status-archived-lightgrey)
![Maintenance: Discontinued](https://img.shields.io/badge/maintained-no-red)


Project Code and instructions for a reboot of a vintage 1980's Robie robot

## Status

> [!WARNING]
> **This project is archived and discontinued.** It is no longer maintained.

A large amount of the code for this project was never pushed to this repo. What is here is a mixture of salvageable components, and very preliminary stuff. 

It dates back to when Robbie was a repurposed vintage robot, driven by Markov chain text generation and crude transformer chatbots (not pushed to this repo). That version is now fully two revisions old: Robbie was redesigned as a 3D printed autonomous robot, and later redesigned again as a stationary device with a moving head.

This repo is kept only as a kind of photo album of the original build.

Specific parts that I am salvaging from this repo:

  - __Round display driver (C++):__ 
     - [code_robbie/cpp/eye_manager/](code_robbie/cpp/eye_manager/)
    - Drives the 1.28" GC9A01 round SPI LCD from a pi (`spi_display/Round_1_28.cpp`).
    - Renders via canvas_ity; has a PC build for testing on the desktop.

  - __Eye animation:__ 
    - [eye_lids.py](code_robbie/eye_manager/eye_lids.py), [eye_renderer_cv2.py](code_robbie/eye_manager/eye_renderer_cv2.py)
    - Blinking eyelid based on curves tuned for a good effect.
  
  - __SPI screens driver using dirty-region updates:__ 
    - [updated_region_finder.py](code_robbie/utils/updated_region_finder.py), [regions_by_fitted_rec_32.py](code_robbie/utils/regions_by_fitted_rec_32.py), [interlaced_graphics_manager.py](code_robbie/utils/interlaced_graphics_manager.py)
    - Only push changed rectangles to the display, and only draw alternate lines.
    - The idea is good, this version of the code is rough and unfinished (a numba specific atrocity).
    - A later version exists that I coded while on a long flight.
  - __Pi 4 docker setup:__ [container_robbie/pi4_base/](container_robbie/pi4_base/)
    - udev rules and Dockerfiles to give a container GPIO / SPI access.
    - This stuff was very fiddly to get working well, and it's useful for any pi hardware project.




## Work
  - __Mechanical:__
    - Done:
      - Head rotation.
      - Front panel assembly, holding pi / camera and screen.
    - In progress
      - arms
      - drive system.
  - __Software:__
    - Done:
       - Robbie is able to tell jokes (from an internal database); mostly using the correct vocal intonations.
       - Robbie is able to give random (often silly) life advice.
       [code for this lives outside the repo]
    - In progress:
       - Random (but sensible) cocktail recipe generation.
       - Pervasive mood.
       - Internal dialogue.
       - Others as ideas hit.
  - __Electrical__:  
       - Done:
         - 2.2" front display is working.
       - In progress:
         - Internal speaker is being re-investigated after some issues.
         - I have not yet ordered a "matrix voice unit" to fit that, and make robbie more interactive. 

__Shout outs__:
  - Brett Downing for hacking on the drive systems and display; as well as floating some awesome ideas.
  - ANU Maker-space for letting me use their 3D printers.

## Rationale
I am unhappy with the "little helpers" of this world (Google, Siri, Alexa). 
They don't feel like the robotic helpers we envisioned in the sci-fi of the 1960's-90's.
They are too:
  - subservient
  - "product like"
  - censored
  - tied to services and apps
  - corporate
  
I want to create something more:
  - Emotive 
  - Self actuated
  - Fun to be around
  - Character driven
  - Independent
  
## Overview

The project is created by opening up an old 'Robie Robot' and gutting it of all the old electronics, motors and lights.  

Then there are four major sections that need to be constructed:
1) Head
2) Front assembly
3) Rear assembly
4) Drive system and battery.

A Bill Of Materials (BOM) is provided and most of the required mechanical components are 3D printable with relevant cad 
and .stl files provided.

After constructing and fitting the different sections, install the software to the pi and close up the unit. 

## Instructions, building the head
The head can be upgraded to rotate via a stepper motor (BOM-04).
I created a mechanical assembly in OpenSCAD to do this and hold a matrix voice module.

__Design__  
![Upper view](doco/pics/head_gears_upper.png?raw=true "Upper view")
![Lower view](doco/pics/head_gears_lower.png?raw=true "Lower view")

__CAD Files__    

    CAD/head_rotary_assembly
Contains .scad and 3D printable .stl files.

__Assembly__  
![Printed parts](doco/pics/P6185662.JPG?raw=true "Printed parts")
The ring gear fits on the inside of the robot's head. The notch on the outside of the ring gear aligns with a key in the robot's plastic.  

![Printed parts](doco/pics/P6185667_close_up.jpg?raw=true "Printed parts")
The brace aligns with the rim under the robot's head.  

![Printed parts](doco/pics/P6185672.JPG?raw=true "Printed parts")
Note: the gear only fits one way round.

__Result__  
Video of the motion of the head in action.  

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/sQd-v5fpN5s/0.jpg)](https://youtu.be/sQd-v5fpN5s)



## Instructions, Front assembly
The front assembly contains a raspberry pi 3 b+ (BOM-03), a pi-cam and 2.2" TFT Display (BOM-01), 
facing through the robot's front port.


__Assembly__
Build Notes:
  - This is deliberately a tight fit, you may need to adjust some bits.

__Design__  
![Upper view](doco/pics/front_asm_render.jpg?raw=true "Upper view")

__CAD Files__    

    CAD/front_assembly
Contains 3D printable .stl files.
  
  

