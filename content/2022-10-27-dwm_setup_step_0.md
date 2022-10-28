+++
title = "dwm Setup (Part 0)"
date = 2022-10-27

[taxonomies] 
tags = ["linux", "configuration"]
+++

## Installing DWM on Fedora 36

First install the Xinerama Library, which does not come by default.

```
sudo dnf upgrade
sudo dnf install libXinerama
```

## Get DWM

```
# get dwm source code
git clone git://git.suckless.org/dwm
```

## Patching DWM for specific features

The following patches are going to be applied:

- [uselessgap](https://dwm.suckless.org/patches/uselessgap/)
- [autostart](https://dwm.suckless.org/patches/autostart/)

Useless-Gap creates some gaps between screens on the desktop layout.

The autostart patch runs `autostart_blocking.sh` within the `~/.dwm/` folder when dwm initializes.

Next download the following patches:
(commands listed below are for the latest patches as of the year 2022)

```
mkdir patches && cd patches
wget https://dwm.suckless.org/patches/autostart/dwm-autostart-20210120-cb3f58a.diff
wget https://dwm.suckless.org/patches/uselessgap/dwm-uselessgap-20211119-58414bee958f2.diff
```

Apply the patches

```
cd dwm
git apply ../patches/*.patch
```

Compile and Install
```
make
sudo make install
```

Now, we have dwm with gaps and autostart.

In the next part, how to add custom status bar and wallpapers will be covered.
