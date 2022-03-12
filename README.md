
This is a fork of [PiClock3](https://github.com/n0bel/PiClock3) that has been modified to be a much simplified version of the desktop clock.

## Here is what the new configuration looks like
![](.README_images/office-clock.png)

## Here is how to make the clock start at boot time:

1. Create a file in your home directory called `piclock3-startup.sh` with this content
````bash
#!/bin/bash
cd /home/your-id-name-here/PiClock3 && python3 ./PyQtPiClock3.py
````
2. Make sure the file is executable
````bash
chmod +x ./piclock3-startup.sh
````
3. Create a file called `/etc/xdg/autostart/piclock3.desktop` with this content
````bash
[Desktop Entry]
Type=Application
Name=PiClock3
Comment=Desktop Clock
NoDisplay=false
Exec=/home/your-id-name-here/piclock3-startup.sh
NotShowIn=GNOME;KDE;XFCE;
````
4. Reboot


## Here is how to remove the cursor from the screen
1. Install the `unclutter` package 
````bash
sudo apt update
sudo apt install unclutter
````
2. Add `@unclutter -idle 0` to `/etc/xdg/lxsession/LXDE-pi/autostart`
````bash
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
@xscreensaver -no-splash
@unclutter -idle 0
````
3. Reboot