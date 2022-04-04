# 🐟 cod 🐟

Standing for **cat or dir**, **cod** is a no-nonsense tool for Linux and other 
*nixes to print stuff out loud, whether it be the contents of a file or the 
files in a directory. Never again waste precious seconds of your life changing 
that **cat** to **dir**, then the other way 'round, just to take a look through 
your files from within the CLI.


# man cod

**Usage:** `cod [someFile] [someDir] [someOtherFile] [...]`

**cod** takes no options. If you write `cod --help` - it will look for a file 
or a directory called `--help`. Likewise for `cod -h`. Because you may actually 
have files like that, and having **cod** in your system means that you already 
very well know what it's there for.

**cod** loops through the arguments sent to it.

If an argument evaluates to a file, **cod** prints the path to the file, then 
prints the file with **cat**.

If an argument evaluates to a directory, **cod** prints the path to the 
directory, then prints the names of its contents, as well as some other useful 
stuff - using **ls -Al**, because it's better than **dir**, and because fish 
aluminum poisoning is a problem, maybe much smaller than many other problems, 
but one nevertheless.

If there are no arguments, **cod** prints the path to the current directory and 
runs **ls -Al** in it.

**cod** is intended for humans, and not further scripts. Get your scripts 
together, it's not that hard.

But if even the human is tired of **cod** constantly printing paths, the 
environment variable **$COD_NONAME** may be set to *1* in order to silence it.


# no pix no clix?

There won't be any. We may have people with CLIs and/or disabilities reading - 
and with **cod**, _those_ are the first-served.

However - we don't really need any. This is what **cod** is like:

```
sh-5.1$ cd /etc/X11
sh-5.1$ cod
/etc/X11:
total 8
-rw-r--r-- 1 root root  92 Feb  3  2017 10-radeon.conf
-rw-r--r-- 1 root root 189 Jan 18  2016 20-radeon.conf
drwxr-xr-x 1 root root  50 Oct 17  2020 xinit
drwxr-xr-x 1 root root  72 Mar 11 16:53 xorg.conf.d
sh-5.1$ cod 20-radeon.conf
20-radeon.conf:
Section "Device"
    Identifier "Radeon"
    Driver "radeon"
    Option "ColorTiling" "on"
    Option "ColorTiling2D" "on"
    Option "DRI" "3"
    Option "AccelMethod" "glamor"
EndSection
sh-5.1$ cod xorg.conf.d xorg.conf.d/*
xorg.conf.d:
total 8
-rw-r--r-- 1 root root 226 Mar  6 16:58 90-xpra-virtual.conf
-rw-r--r-- 1 root root  54 Feb  2  2020 99-virtualgl-dri
xorg.conf.d/90-xpra-virtual.conf:
# Ignore all xpra virtual devices by default,
# these will be enabled explicitly when needed.
Section "InputClass"
        Identifier "xpra-virtual-device"
        MatchProduct "Xpra"
        Option "Ignore" "true"
EndSection
xorg.conf.d/99-virtualgl-dri:
Section "DRI"
	Mode 0660
	Group "vglusers"
EndSection
```

# Wow, how do I install?

Use your favorite package manager. Oh wait, we're not in your repos yet? Ookay, 
then you can do it something like this:
```
sudo wget -P /usr/local/bin raw.githubusercontent.com/newbthenewbd/cod/main/cod
sudo chmod +x /usr/local/bin/cod
```
You're a CLI person. You can do it.


# License?

MIT.


# Want moar inventions of yours, where do I donate?

Here:

[Donate with PayPal, or a bankin' card apparently](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=sendmoney%40go2%2epl&lc=US&item_name=Express%20gratitude%20for%20cod%20with%20a%20donation&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted)

(Okay, that one's pretty difficult to do on the CLI... Sorry.)

(Also, did you know that you can modify that link in some interesting ways?)

(Like, to send a different currency... Klingon darseks unavailable, I'm afraid)

Seriously though be advised, I'm just a poor busy dude going through uni at the 
time of this writing, so while I am truly very thankful for even your 
considering of any donation whatsoever, this might just not make me any more 
productive... :-)
