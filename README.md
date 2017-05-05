TIDA: Ubuntu
====

Things I Did After Installing Ubuntu. This is a reference for all the thing I do after a clean install of Ubuntu.

# Useful commands and other tips:

**Useful commands**

```bash
lsusb
dmesg | grep tty
ubuntu-bug -w

# since 14.04 the apt commando has support for all the things apt-get apt-cache etc can do.
# but apt does it better and with nicer output
apt search
apt install

# have you tried to run a command but forgot "sudo"? "!!" means "previous command"
sudo !!
```

**Image editing**

To crop an image: right-click on it. Click on "open with" > "Shotwell viewer". This program has simple picture tools such as crop, red-eye, enhance, rotate.

**Shortcuts**
```
# To have tiling-like abilities:
ctrl-alt-numpad_key

# Select area to make screenshot from, screenshot is automatically saved in clipboard
ctrl-shift-printscreen

# To search in the applications menu (very handy in gimp!)
press alt and start typing
```

# Bugfixes

**Software Center**

**Workaround**
The software center is still extremely buggy and in a poor state. It crashes a lot on .deb files from the internet. I recommend setting gdebi as default application to open .deb packages.

```
apt install gdebi
```
Then go to "Files" right-click a .deb file. Click on "properties". Go to tab "open with". Click on gdebi package installer and click on "set as default". Be sure to do this in the "properties" window. Otherwise, you will not see the "set as default" option.

**List of bugs**

This is a list of all the software center bugs currently affecting me. Feel free add yourself to the affected list to get more traction

   * [Free applications having "buy" button instead of "install"](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/968974) *Related:* [Why do I have to sign in into Ubuntu One when installing free apps](http://askubuntu.com/questions/319091/why-do-i-have-to-sign-into-ubunto-one-in-order-to-install-steam)



# Restricted Extras

## DVD PLAYBACK

https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs

## Oracle Java

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt install oracle-java7-installer
```

[source](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

## Fonts:

Extract fonts.zip to home directory (this zip cannot be included here due to copyright issues). MS fonts tend to look very ugly when they are small. Following fix disables that behavour:

Edit `~/.config/fontconfig/fonts.conf`

Add following lines:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- $XDG_CONFIG_HOME/fontconfig/fonts.conf for per-user font configuration -->
<!-- http://www.freedesktop.org/software/fontconfig/fontconfig-user.html -->
<fontconfig>
    <!-- Prevent Gnome from using embedded bitmaps in fonts like Calibri -->
    <match target="font">
        <edit name="embeddedbitmap" mode="assign"><bool>false</bool></edit>
    </match>

    <!-- Reject bitmap fonts in favour of Truetype, Postscript, etc. -->
    <selectfont><rejectfont><pattern>
        <patelt name="scalable"><bool>false</bool></patelt>
    </pattern></rejectfont></selectfont>

    <!-- Substitute truetype fonts for bitmap ones -->
    <match target="font">
        <edit name="prefer_outline"><bool>true</bool></edit>
    </match>
</fontconfig>
```

## MS Office

Use version of wine >1.5.17 (fixed font antialising bug)
install the following components (very easy to do with playonlinux):
- ‘Microsoft Core Fonts’  -> (not needed if you add the fonts in a different way)
- ‘Disable Crash Dialog’  -> (not needed)
- ‘FontSmoothRGB’         -> Font antialising
- LunaTheme               -> winxp theme
- ‘Tahoma’                -> (not needed if you add the fonts in a different way)

[source](http://rmitc.org/2013/04/ultimate-microsoft-office-2010-installation-on-ubuntu/comment-page-1)

## Google-talk plugin
GOOGLE TALK PLUGIN


# Tweaks

**Preload: load programs in memory for faster startup**
```
sudo apt install preload
```

**Power saving**

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt update
sudo apt install tlp tlp-rdw
sudo tlp start
```


**Caffiene, disables screensaver when app is fullscreen (like youtube video)**

```
sudo apt install caffeine
```

**Native GTK themes with qt, and other things (like skype)**
```bash
sudo apt install gtk2-engines

# only for 64 bit:
sudo apt install gtk2-engines-murrine:i386
sudo apt install gtk2-engines-pixbuf:i386

# indicator support for qt applications in 64-bit ubuntu
sudo apt install sni-qt
```


# GOOD APPLICATIONS

Pinta image editor, Linux paint alternative

```
sudo apt install pinta
```

VLSub, automatic subtitle download extention for vlc media player

```
sudo apt install vlc-plugin-vlsub
```

# PROGRAM SPECIFIC TWEAKS

#GIT
**Use colors**
git config --global color.ui auto

**Use password manager**


#Things to configure	
**Local menus**

appearence > behaviour

**Smaller launcher**

**Language and regional settings**

#Security

```
sudo ufw enable
sudo apt install gufw
```

#VPN

```
sudo apt install network-manager-openvpn network-manager-openvpn-gnome
```
in network manager => vpn => add vpn
