# Raspberry Pi 3 Server Install and Setup
First things first lets install the OS on the RPi3 (Raspberry PI 3) Server and get it functioning then we will move on to hooking all the hardware up in the box later. 

# RPi3 Base Install Directions (MAC)

Format SD card using SDformatter
https://www.sdcard.org/downloads/formatter_4/eula_mac/index.html

Download Raspian Noobs
If OLD like me you know what to do:
Install and boot

If NEW then do this:
Download Noobs onto your computer
Unzip and copy Noobs contents to root folder on newely formatted SD card
Plug in HDMI, mouse, keyboard and ethernet (unless you use wifi) to RPi3
Put SD card into PI3 and plug it in (Remember 5V 2-2.5amp Power Supply ONLY for RPi3 DO NOT PLUG INTO 12V PS)
On initial boot Noobs will as you to connect to your wifi (if used). Do this first!
Once connected Noobs will ask you which OS to install. Choose Raspian! (now wait about an hour for it to decompress)
Once rebooted you will be in GUI interface, start command prompt and type the following command

: sudo raspi-config

Once raspi-config menu loaded do this:
Change password for user pi to whatever you want
In Advanced options - Change Memory allocation to 16
In Advanced options - Change RPi3 name to whatever, I use RPi3HAS for server and RPi3HACx (x=client box ID number).
In Advanced options - Turn off i2C
In Advanced options - Turn off SPI
In Advanced options - Turn off Serial
Save and Reboot

Login with user Pi password you changed prompt should not look like this if you use my server name)
pi@RPi3HAS:

# Static IP address setup
If you decide to set a static IP address (I Do) then see the following article is it outside the scope of this document. If you are unsure of static IP addressing then leave as is. Eventually, you will want to assign static IP addresses to your system but you have to be aware of Ip addressing schemes and subnet masking, etc. before going there. Here is a good link on how to change it once you know what you want.

https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update

# Dynamic IP Addresssing (Default)
Nothing to do if using dynamic but watch the IP address it can change over time depending on your DHCP server.

Now the RPi should have rebooted and you should be in the GUI interface again. Be sure to connect to your wireless again in top right corner of screen. Then drop to command line and use the folowing commands:

: sudo apt-get update
: sudo apt-get upgrade (watch for y/n prompts and answer "yes")
: sudo apt-get install rpi-update
: sudo rpi-update
: sudo reboot (reboot after updates)




# Step 2 Install MQTT Broker
Now it is time to install the Broker. In my setup the Broker is the Server and I will not have it doing any relay switching itself. It will only serve as OpenHab and MQTT Broker server. So I will only be installing the MQTT Broker and Not the Client on this RPi.

: sudo apt-get install Mosquitto (Use the apt-get method and not manual it puts everything in the right directories)



raspi-config (or preferences in graphical interface)
change password
select to boot to CLI

select timezone/keyboard
select GPU to 16

reboot
sudo apt-get update
sudo apt-get upgrade
sudo rpi-update

##Openhab2

echo 'deb https://openhab.ci.cloudbees.com/job/openHAB-Distribution/ws/distributions/openhab-offline/target/apt-repo/3 /' | sudo tee /etc/apt/sources.list.d/openhab2.list
echo 'deb https://openhab.ci.cloudbees.com/job/openHAB-Distribution/ws/distributions/openhab-online/target/apt-repo/1 /' | sudo tee --append /etc/apt/sources.list.d/openhab2.list

wget -qO - 'http://www.openhab.org/keys/public-key-snapshots.asc' | sudo apt-key add -

sudo apt-get install apt-transport-https

#RPi3 Base Install Directions (Windows)

Format SD card using SDformatter
https://www.sdcard.org/downloads/formatter_4/eula_windows/index.html

install disk image using win32diskimager (raspian)

install and boot
raspi-config (or preferences in graphical interface)
change password
select to boot to CLI

select timezone/keyboard
select GPU to 16

reboot
sudo apt-get update
sudo apt-get upgrade
sudo rpi-update

##Openhab2

echo 'deb https://openhab.ci.cloudbees.com/job/openHAB-Distribution/ws/distributions/openhab-offline/target/apt-repo/3 /' | sudo tee /etc/apt/sources.list.d/openhab2.list
echo 'deb https://openhab.ci.cloudbees.com/job/openHAB-Distribution/ws/distributions/openhab-online/target/apt-repo/1 /' | sudo tee --append /etc/apt/sources.list.d/openhab2.list

wget -qO - 'http://www.openhab.org/keys/public-key-snapshots.asc' | sudo apt-key add -

sudo apt-get install apt-transport-https
