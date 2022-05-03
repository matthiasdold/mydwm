# General Idea
This repo is ment as notes for myself as of how to setup my dwm rice
![screenshot](./screenshot.png)

## Base components
* dwm
* dwmblocks
* st 
* patches as specified below

# Git Management
Follow [this idea](https://dwm.suckless.org/customisation/patches_in_git/), 
the basic idea is to have a branch for each patch and then merge them together.
For this reason, I did start a new branch for each of my patches and later merged
them within a `mydwm` branch. This later one also contains my personalized config for the keys.

# St
Starting with st as this is rather simple

```bash
git clone https://git.suckless.org/st
```

#### Patches

* [alpha](https://github.com/juliusHuelsmann/st/releases/download/v2/st-focus-20200731-patch_alpha.diff) -> have transparency in the terminal
* [alpha_focus](https://github.com/juliusHuelsmann/st/releases/download/v2/st-focus-20200731-43a395a.diff) -> different transparency depending on focus 
* [scrollback](https://st.suckless.org/patches/scrollback/st-scrollback-20210507-4536f46.diff) -> scrolling back in the terminal with SHIFT+PgUp/Down
* [scrollback_mouse](https://st.suckless.org/patches/scrollback/st-scrollback-mouse-20220127-2c5edf2.diff) -> scrolling in the terminal with the SHIFT+Mousewheel
* [font2](https://st.suckless.org/patches/font2/st-font2-20190416-ba72400.diff) -> better rendering for some powerline fonts
* [ligatures](https://st.suckless.org/patches/ligatures/) -> nicer font with ligatures
* [nordtheme](https://st.suckless.org/patches/nordtheme/) -> the basic colorscheme I use
* [moonfly](https://st.suckless.org/patches/moonfly/) -> potential alternative to nord

# Get dwm

```bash
git clone https://git.suckless.org/dwm
```

# Patches and reasons why
* [Vanitygaps](https://dwm.suckless.org/patches/vanitygaps/dwm-cfacts-vanitygaps-6.2_combo.diff) -> eye candy for gaps and included cfacts for better resizing
* [status2d](https://dwm.suckless.org/patches/status2d/) -> all patches to work without any extra tool / program for status
* [xrdb](https://dwm.suckless.org/patches/xrdb/dwm-xrdb-6.2.diff) -> xrdb colors, also used within status2d
* [statusallmons](https://dwm.suckless.org/patches/statusallmons/dwm-statusallmons-6.2.diff) -> statusbar on all monitors
* [alpha](https://dwm.suckless.org/patches/alpha/dwm-alpha-20201019-61bb8b2.diff) -> Transparency in bar
* [setstatus](https://dwm.suckless.org/patches/setstatus/dwm-setstatus-6.2.diff) -> simpler syntax for setting the status bar
* [hide_vacant_tags](https://dwm.suckless.org/patches/hide_vacant_tags/dwm-hide_vacant_tags-6.2.diff) -> show only tags with some client on them (not 1 2 3...9 all the time)
* [scratchpads](https://dwm.suckless.org/patches/scratchpads/dwm-scratchpads-20200414-728d397b.diff) -> Use scratchpad for journaling notes

# Manually patching
Some(often)times a patch fails to be applicable straigth away. I had the issue with vanity following the deck version of cfacts e.g..
In this case, I did apply the steps manually for the files with error. Later the changes
can be recorded to a `.diff` via 
````bash
git diff HEAD^ > my_patch_file.diff
````

## Patch to vanilla

# dwmblocks
I use this as for my quick research, it was the only one really using separate refresh cycles for its components. 
So it seemed to be the best fit - [dwmblocks](https://github.com/ashish-yadav11/dwmblocks)
``` bash
git clone git@github.com:ashish-yadav11/dwmblocks.git
```
## Installation
-> Apply the patch to dwm
-> Add `dwmblocks &` to the `~/.xinitrc`
## Modules
As opposed to Luke Smith's build, I will now keep the modules within `./dwmblocks/blocks.def` but making use of Lukes build, and adding the functions as patches
### Install note
- Make sure to properly patch dwm for the update to work!
- The individual scripts are part of the patch `my_full_dwmblocks*`...

### pacpackages
The pacpackages needs something like a chron job to run `pacman -Sy` every now an then. I used the native are `systemd timers`.
From within the `dwmblocks/blocks.def` directory do:
```
cp pacpackages.service /etc/systemd/system
cp pacpackages.timer /etc/systemd/system
systemctl enable pacpackages.timer
systemctl start pacpackages.timer

```

## 

# TODO
* Clickable statusbar --> something with [this](https://dwm.suckless.org/patches/statuscmd/)
