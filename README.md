TIDA: Ubuntu 14.04 Trusty Tahr
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
```

**Image editing**

To crop an image: right-click on it. Click on "open with" > "Shotwell viewer". This program has simple picture tools such as crop, red-eye, enhance, rotate.

**Shortcuts**
```
# To have tiling-like abilities:
ctrl-alt-numpad_key

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

## HTML5 video in FireFox
```bash
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

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
<match target="font" >
<edit name="embeddedbitmap" mode="assign">
<bool>false</bool>
</edit>
</match>
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

## Silverlight

[source](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

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

**Nvidia Optimus support**

```
sudo apt purge bumblebee*
sudo apt install nvidia-prime
```

**Caffiene, disables screensaver when app is fullscreen (like youtube video)**

```
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt update; sudo apt install caffeine
```

**Native GTK themes with qt, and other things (like skype)**
```bash
sudo apt install gtk2-engines

#only for 64 bit:
sudo apt-get install gtk2-engines-murrine:i386
sudo apt-get install gtk2-engines-pixbuf:i386
```



# PROGRAM SPECIFIC TWEAKS

##SUBLIME TEXT

**Install**

```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt update
sudo apt install sublime-text-installer
```

**Build shell**

```
{
    "cmd"       : ["$file"],
    "selector"  : "source.shell",
    "shell"     : "bash"
}
```

[source](http://www.webupd8.org/2013/11/y-ppa-manager-0992-adds-support-for.html)

**Build c++**
sudo apt install build-essential

#GIT
**Use colors**
git config --global color.ui auto

**Use password manager**


#Things to configure	
**Local menus**

appearence > behaviour

**Smaller launcher**

**Language and regional settings**

**Webgl support chrome**

Step 1: Open Google Chrome

Step 2: Type chrome://flags in the address bar

Step 3: Press Ctrl + f and type ” Rendering list “, “Override software rendering list” should come up, Now click on Enable and restart the browser.

Now check chrome://gpu/


#Security

```
sudo ufw enable
sudo apt install gufw
```

#VVS	
##VPN

```
sudo apt install network-manager-openvpn network-manager-openvpn-gnome
```
in network manager => vpn => add vpn

##Ipv6

```
sudo apt install aiccu
```
sudo aiccu start


#UGENT

`sudo apt install network-manager-vpnc`

[source](https://helpdesk.ugent.be/vpn/linux.php)


#DEPRECATED

Did not use anymore, maybe in the future?

## disable touchpad when external mouse
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt update; sudo apt install touchpad-indicator
```

##CITRIX

```
mkdir ica_temp
dpkg-deb -x icaclient_ ica_temp
dpkg-deb --control icaclient_ ica_temp/DEBIAN
sudo gedit ica_temp/DEBIAN/control
	Depends: libc6-i386 (>= 2.7-1), lib32z1, nspluginwrapper
dpkg -b ica_temp icaclient-modified.deb
sudo dpkg -i icaclient-modified.deb
sudo apt install -f
sudo gedit /var/lib/dpkg/info/icaclient.postinst
	echo $Arch|grep -E "i[0-9]86|x86_64" >/dev/null
sudo apt install -f
sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts
```
https://help.ubuntu.com/community/CitrixICAClientHowTo

http://ubuntuforums.org/showthread.php?t=2166020&page=4






