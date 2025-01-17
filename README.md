# ACES ODT Candidates
 Prebaked LUTs of the ACES 2.0 ODT candidates from the [ACES Output Transforms Architecture Virtual Working Group](https://paper.dropbox.com/doc/Output-Transforms-Architecture-Virtual-Working-Group-HKNpj824NA0Z8tn7jiPS0)

This repo contains:
* a Nukescipt used to bake the LUTs.
* A dctl template to wrap them in a way Resolve will treat as a valid ACES ODT.
* A FilmLight Display Rendering Transforms intended for use in Baselight.

There is a HDR YouTube clip comparing these 3 versions [here](https://www.youtube.com/watch?v=s8f1MylJLN0). It should only be viewed on a HDR display, as SDR playback will be passing through YouTube's tonemapper, which dramatically effects the look.



# Installation

## OCIO for Nuke and other Applications

There is a cutdown OCIO config based on the current ACES 1.2 config.
It includes all Input and Utility spaces, but a greatly reduced set of Output spaces.

There are two config variations:
* A standard `config.ocio` for general use in Nuke on Linux and Windows, and other generic OCIO applications.

* And a second `condig_DisplayP3.ocio` intended for use with Nuke 13 on a Mac with EDR support.
This can be enabled via the `Preferences -> Color Management -> Enable macOS HDR Color Profile` checkbox, and setting the `gl buffer depth` to `half-float` in the Viewer settings pane.



## Filmlight Baselight

### 1. Adding the DRTs to Baselight:
- Copy all the files contained in `ACES2_0_Candidates_rev007` to `/vol/.support/etc/colourspaces`
- Restart Baselight
- You should see three new custom DRTs in `Scene Settings -> Format & Colour -> Display Rendering Transform`


## Davinci Resolve

### 1. Adding a Custom ACES IDT or ODT File:
- Navigate to the `ACES Transforms` folder in Resolve's application support folder.
    - MacOS: `~/Library/Application Support/Blackmagic Design/DaVinci Resolve/ACES Transforms`
    - Windows: `C:\Users\<User>\AppData\Roaming\Blackmagic Design\DaVinci Resolve\Support\ACES Transforms\IDT`
    - Linux: `~/.local/share/DaVinciResolve/ACES Transforms`
- Place your custom ACES DCTL files for Input Device Transforms (IDTs) in the IDT subfolder.
- Place your custom ACES DCTL files for Output Device Transforms (ODTs) in the ODT subfolder.
- Start Resolve.
