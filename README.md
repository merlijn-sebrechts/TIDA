TIDA: Ubuntu 14.04 Trusty Tahr
====

Things I Did After Installing Ubuntu. This is a reference for all the thing I do after a clean install of Ubuntu.



# Useful commands

`lsusb`
`dmesg | grep tty`
`ubuntu-bug -w`

# Restricted Extras

## DVD PLAYBACK

https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs

## Oracle Java

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
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
- LunaTheme                  -> winxp theme
- ‘Tahoma’                     -> (not needed if you add the fonts in a different way)

[source](http://rmitc.org/2013/04/ultimate-microsoft-office-2010-installation-on-ubuntu/comment-page-1)

## Silverlight

[source](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

## Google-talk plugin
GOOGLE TALK PLUGIN




# Tweaks

**Preload: load programs in memory for faster startup**
```
sudo apt-get install preload
```

**Power saving**

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
sudo tlp start
```

**Nvidia Optimus support**

```
sudo apt-get purge bumblebee*
sudo apt-get install nvidia-prime
```

**Caffiene, don't sleep when flash video**

```
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update; sudo apt-get install caffeine
```

**Native GTK themes with qt**
```
sudo apt-get install gtk2-engines
```



# PROGRAM SPECIFIC TWEAKS

##SUBLIME TEXT

**Install**

```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
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
sudo apt-get install build-essential

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
sudo apt-get install gufw
```

#VVS	
##VPN

```
sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome
```
in network manager => vpn => add vpn

##Ipv6

```
sudo apt-get install aiccu
```
sudo aiccu start


#UGENT

`sudo apt-get install network-manager-vpnc`

[source](https://helpdesk.ugent.be/vpn/linux.php)


#DEPRECATED

Did not use anymore, maybe in the future?

## disable touchpad when external mouse
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update; sudo apt-get install touchpad-indicator
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
sudo apt-get install -f
sudo gedit /var/lib/dpkg/info/icaclient.postinst
	echo $Arch|grep -E "i[0-9]86|x86_64" >/dev/null
sudo apt-get install -f
sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts
```
https://help.ubuntu.com/community/CitrixICAClientHowTo

http://ubuntuforums.org/showthread.php?t=2166020&page=4






