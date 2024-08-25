# KliPiNP: Klipper Pi PNP Configuration

## Overview

KliPiNP is a unique blend of Klipper firmware with OpenPNP, aimed at optimizing the functionality and adaptability of pick-and-place systems. 

### Why This Project?

The rationale behind KliPiNP hinges on several key technical insights:

- **Uncharted Territory**: No one else has married Klipper's firmware capabilities with OpenPNP's handling precision in this way before. KliPiNP aims to set a precedent, creating a new standard for what open-source hardware can achieve in automated systems.

- **Comfort with Klipper**: The decision to utilize Klipper stems from a deep familiarity with its ecosystem. This comfort level allows for a more intuitive setup, quicker troubleshooting, and smoother operation overall.

- **Config on the Fly**: Klipper excels in allowing users to tweak and adjust settings without the downtime of reflashing firmware—crucial in an environment where quick adjustments can be the difference between an optimal or subpar performance.

- **Mechanical Smoothing**: The project uses a Lumen style frame, a low cost flexible Pick and Place platform. Klipper's input shaper comes into play here, effectively dampening any frame-induced vibrations or noise, thus ensuring high precision without the need for heavy-duty frame enhancements.

- **Macro-based Simplification**: The use of Klipper macros significantly streamlines the kinematic setup. For example, integrating a 'HOME-ALL' macro means homing becomes a one-command operation in the system. This simplicity extends to OpenPNP, where either system's macro capabilities can be used to tailor the workflow to specific needs.


# Build Notes
 A collection of lessons learned, tools used and techniques employed to make this possible

## Hardware 
- Everything to build a Lumen PNP. I purchased everything over a  period of time and let it collect dust for several months. I probably should have just coughed up the dough to buy a kit from Opulo. But whats the fun in that. https://www.opulo.io/
- Bigtree tech Octopus max EZ  https://github.com/bigtreetech/Octopus-Max-EZ
- Raspberry Pi 5 (8GB) https://www.raspberrypi.com/products/raspberry-pi-5/
- NVMe hat to attach a 256GB SSD https://www.adafruit.com/product/5845
- Misc hardware, nuts, bolts, stepper motors (salvaged from several ender 3 3d printers), LEDs  etc

## Software Requirements
- Klipper firmware https://www.klipper3d.org/
- OpenPNP https://github.com/openpnp/openpnp
- Debian Linux distro 

## Installation
Installation of Klipper and OpenPNP is very well documented
Refer to the respective installation guides to get familiar with installation process

### General notes
- If you are building a P&P for a custom build, make sure you get a controller board that can support the number of steppers you intend to use
- I opted to mod the Lumen to use 2 motors each for the X and Y axis.
- Your build determines the Klipper configuration. This is obvious, but I wanted to make sure to pint that out. DO NOT blindly use my configuration.
- The details provided here are for documentation and refernce purposes only. No warranty is provided on any information provided here.
- I am running both OpenPNP and Klipper on the same Raspberry Pi 5. This is kinda important, and the main point of this use case. If you are running OpenPNP on a different device and Klipper on a different device, then you have lost the plot :)

### Klipper specific items
- If you are building a 1 head P&P, you may be able to use the official Klipper repo. Howver, I was building a 2 head P&P. So I used a fork of Klipper that has support for XYZABC axis configuratoion.
- The fork i used is here : https://github.com/naikymen/klipper-for-cnc
- See the repo for the installation insdtructions : https://github.com/naikymen/klipper-for-cnc?tab=readme-ov-file#installation
- Official Klipper repo is here : https://github.com/Klipper3d/klipper
- There are several videos and sites which explain klipper installation, such as this writeup https://klipper.discourse.group/t/installing-klipper-with-kiauh/10734
- Build your firmware for the controller board you are going to use. Most boards that can be flashed with Marlin can also be used with Klipper. YMMV
  
## Configuration
Detail the configuration steps specific to getting Klipper and OpenPNP working together.

- Getting Klipper to talk to OpenPNP was surprisingly simple.
- OpenPNP can talk to a controller either using Serial (USB) or TCP
- Klipper provides a "virtual Serial port" that we can use, but we will use it over TCP
- Make sure you are able to run this command in a Linux bash shell
 ` sudo socat TCP-LISTEN:5000,reuseaddr,fork OPEN:/dev/pts/0,append`
- If you get any errors, try using `sudo apt install socat` before you run the command
- keep the terminal window open once you hit enter. This will keep the socket alive between Klipper and OpenPNP

## Usage
Explain how to use the system once it's configured.

## Contributing
Invite others to contribute and explain how they can do so.

## License
Specify the license under which your project is released.

## Contact
Provide a way for users to reach you for further inquiries or support.

## Gallery
Embed images or videos showing the setup in action.