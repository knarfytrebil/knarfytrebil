+++
title = "dwm Setup (Part 1)"
date = 2022-10-28

[taxonomies] 
tags = ["linux", "configuration"]
+++

Continued from [Part 0](/dwm-setup-step-0), in this part the following topics will be covered:

- barpadding
- wallpapers


## Applying the patch "Barpadding"
Applying the patch will likely end up in failure, since the patch is made for a previous version of dwm, and some slight change in one of the lines in the file `dwm.c` made the patching command fail. 

So, the next step is to make some changes to "patch the patch".
Now it is time to modify this file: `dwm-barpadding-20211020-a786211.diff`, which could be downloaded from [this page](https://dwm.suckless.org/patches/barpadding/).

then do the following change:

```
-static int bh, blw = 0; /* bar geometry */
+static int bh = 0; /* bar height */
```

This is will make it possible to apply the patch.

When the patch succeeds, do:

```
make
sudo make install
```

## Setting Wallpaper

Install feh

```
sudo dnf install -y feh
```

Edit `~/.dwm/autostart_blocking.sh` insert the following:

```
feh --no-fehbg --bg-fill ~/path/to/your/wallpaper
```

In the end, press `Ctrl + Shift + Q` to restart dwm and we are done.


In the next part, I will try to reconfiture `dmenu` and try using `lemonbar` as the status bar.
