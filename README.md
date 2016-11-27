# OH2-MQTT-RPi3-HA-Server-Kit
This will be the home server box.

# Hardware Used in This Project

Raspberry PI 3 (Barebones Model)
https://www.amazon.com/gp/product/B01CD5VC92/ref=as_li_tl?ie=UTF8&tag=g0573-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B01CD5VC92&linkId=f37fbe61b011fb8df6bf544057cfcb60
<br />
Raspberry PI 3 (with Power Supply, Heat Sinks and Case)
https://www.amazon.com/gp/product/B01C6EQNNK/ref=as_li_tl?ie=UTF8&tag=g0573-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B01C6EQNNK&linkId=8ea8539b42340e07b4a13acc7275c49d"

# RPi3 Base Install Directions (MAC)
Setup
Format SD card using SDformatter

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

#RPi3 Base Install Directions (Windows)

Format SD card using SDformatter
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
