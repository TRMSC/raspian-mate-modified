# raspian-mate-modified
Install RaspianOS with a customizable mate-desktop and some modern stylesheets. 

'Mate' runs fast on the Raspberry Pi 3b+ or higher. You also can install cinnamon-desktop for more modern customization but you will maybe loose bits of speed: https://github.com/TRMSC/raspian-cinnamon-modified

There is plan for making a theme or an image in this repository. Till then you can use the description in this file. 

![htm-mode](https://raw.githubusercontent.com/TRMSC/raspian-mate-modified/main/thumbnail.png)

The wallpaper on the image in this repository is from https://wallpaper.dog/dark-linux-mint-wallpapers. Got inspirations for this article from https://ubuntu-mate.community/t/how-to-install-a-minimal-mate-desktop-on-your-raspberry-pi/16077


------------------------------------------------

1. Download the image:

Get the latest RaspianOS LIGHT-image on
https://www.raspberrypi.org/software/operating-systems/

Flash the image on a SD-Card.


------------------------------------------------

2. First settings

Login - userame: pi - password: raspberry
(if it doesn't work you have to use a 'z' instead of the 'y')

    sudo raspi-config

Localitation options:
- NO LOCALE at this moment
- Select time-zone 
- Change keyboard layout (for example Generic 105-Key-PC). Press enter even if the correct one is marked.
- Select wifi-country
- Press escape

Make a reboot.

    sudo reboot now
        
      
------------------------------------------------

3. WiFi

If you have an internet-connecion by lan-cable you can skip this step.

    sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

Add to the end of the file:

    network={
        ssid="networkname"
        psk="networkpassword"
    }

Press CTRL+O - Enter - CTRL+X

    sudo reboot now


------------------------------------------------

4. Select language

Now you can change the language.

    sudo raspi-config

Localitation options - Change Locale:
- Select with space for example en_US.UTF-8 or de_DE.UTF-8.
- Unselect the languages you don't need if they are selected.
- Press enter.
- Select the default language und press enter again.
- Press escape when finished.

Make a reboot.
    
    sudo reboot now
    

------------------------------------------------

5. Update & Upgrade

Let's do an update and upgrade.

    sudo apt update && sudo apt-upgrade -y


------------------------------------------------

6. User

Create a new user for example 'monica':

    sudo useradd -m monica -G sudo

Select a password:

    sudo passwd monica

    sudo reboot now


------------------------------------------------

6. Login

Login with your new useraccount.

If you want you can delete the pi-user by typing in:

    sudo deluser -remove-home pi
    sudo rm /etc/sudoers.d/010_pi-nopasswd


------------------------------------------------

7. Install the desktop

Now everything is done for installing

    sudo apt install mate-desktop mate-desktop-environment-core mate-themes mate-session-manager xinit mate-terminal mate-applets software-properties-gtk xserver-xorg lightdm pluma --no-install-recommends
    
    sudo apt-get install mate-tweak engrampa
    
Make a reboot:

    sudo reboot now


------------------------------------------------

8. Style the panel

You can start your changes by removing everything on the bottom panel:
- Rightclick on the stuff - unselect 'Lock Panel'
- Delete

Style the panel:
- Rightclick on the panel - Properties
- Change the size to a higher level
- On top of the popup go to 'Background'
- Select 'Solid Color' and change the color
- Use the slider to give your panel transparency

Add stuff to the panel:
- Rightclick on the panel - 'Add to panel'
- A menu as only one butto is called 'Main Menu'
- A menu like on the top-panel is called 'Menu Bar'
- Rightclick on the menu - move (eg to the right)
- You can add a clock to the right 
- If you go to your apps in menu you can add them to the panel by doing a rightclick - 'Add this launcher to panel'

If you want you can delete the top panel now.


------------------------------------------------

9. Theme and background

Now you can choose a theme and etablish a background:
Menu - System - Preferences - Look and feel - Appearance

You can get more themes on the internet.


------------------------------------------------

10. More changes

- For unshowing desktop icons go to Menu - System - Preferences - Look and feel - Mate Tweak


------------------------------------------------

11. Optional packages

You have a distribution without recommended software. If you want you can for example install the following tools:

    sudo apt-get install chrome-browser #browser
    sudo apt-get install firefox-esr #browser
    sudo apt-get install geany #editor
    sudo apt-get install gnome-utils #eg screenshot-tool
    
