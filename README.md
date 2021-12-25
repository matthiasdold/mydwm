# General Idea
This repo is ment as notes for myself as of how to setup my dwm rice

## Base components
* dwm raw
* dwm blocks
* patches as specified below

# Git Management
Follow [this idea](https://dwm.suckless.org/customisation/patches_in_git/)
The basic idea is to have a branch for each patch and then merge them together.
For this reason, I did start a new branch for each of my patches and later merged
them within a `mydwm` branch. This later one also contains my personalized config for the keys.



# Patches and reasons why
* [Vanitygaps](https://dwm.suckless.org/patches/vanitygaps/dwm-cfacts-vanitygaps-6.2_combo.diff) -> eye candy for gaps and included cfacts for better resizing
* [status2d](https://dwm.suckless.org/patches/status2d/) -> all patches to work without any extra tool / program for status
* [xrdb](https://dwm.suckless.org/patches/xrdb/dwm-xrdb-6.2.diff) -> xrdb colors, also used within status2d
* [statusallmons](https://dwm.suckless.org/patches/statusallmons/dwm-statusallmons-6.2.diff) -> statusbar on all monitors
* [alpha](https://dwm.suckless.org/patches/alpha/dwm-alpha-20201019-61bb8b2.diff) -> Transparency in bar
* [setstatus](https://dwm.suckless.org/patches/setstatus/dwm-setstatus-6.2.diff) -> simpler syntax for setting the status bar

# Manually patching
Some(often)times a patch fails to be applicable straigth away. I had the issue with vanity following the deck version of cfacts e.g..
In this case, I did apply the steps manually for the files with error. Later the changes
can be recorded to a `.diff` via 
````
git diff HEAD^ > my_patch_file.diff
````

# dwmblocks
I use this as for my quick research, this was the only one really using separate refresh cycles for its components. So it seemed to be the best fit
## Installation
-> Apply the patch to dwm
-> Add `dwmblocks &` to the `~/.xinitrc`
## Modules
As opposed to Luke Smith's build, I will now keep the modules within `./dwmblocks/blocks.def` but making use of Lukes build, and adding the functions as patches
### Install note
- Make sure to properly patch dwm for the update to work!


# TODO
*
* Clickable statusbar --> something with [this](https://dwm.suckless.org/patches/statuscmd/)
