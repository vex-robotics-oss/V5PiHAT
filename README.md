# V5PiHAT
This repository contains documentation, setup scripts and software examples need to integrate the V5 PiHAT with the VEX V5 robot control system.

# Requirements
1. Window 10
2. V5Hat
3. Rapberry Pi Zero W
   https://www.raspberrypi.org/products/raspberry-pi-zero-w/
4. Raspberry Pi Camera V2
   
5. A 5.25V 2.5A USB micro power supply
6. A USB type A to micro cable
7. At least an 8GB micro SD card
8. A micro SD card do USB adapter
9. A monitor with either an HDMI port or display port.
10. A mini HDMI to HDMI or Display Port cable.
# Hardware Setup

# Loading OS
1. Download Raspian Stretch Lite https://www.raspberrypi.org/downloads/raspbian/
2. Download and install Etcher https://www.balena.io/etcher/
3. Connect the uSD to the computer using the adapter or other method
4. Type BalenaEtcher into the start menu and click BelenaEtcher
5. Click the Select Image Button
6. Navigate to and select the Raspian Stretch Light zip file
7. Click Select Drive
8. Navigate to and select the uSD folder
9. Click the Flash! button and wait for the program to complete

# Configuring the Raspbian for SSH
1. Make sure the uSD card is connected to the computer
2. Create a new text file and save it as ssh in the boot directory of the uSD card
3. Create another file named wpa_supplicant.conf
4. Open the file and type the following substituting wifi_ssid with your wifi ssid and password with your wifi passward:
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
   ssid="wifi_ssid"
   scan_ssid=1
   psk="password"
   key_mgmt=WPA-PSK
   }

5. Save the file  as wpa_supplicant.conf in the boot directory
6. Insert the uSD card into the Raspberry Pi
7. Plug the mini HDMI cable into the Raspberry Pi and connect the other end to a monitor
8. Plug the 2.5A power supply into the Raspberry Pi
9. Record the IP address of the Raspberry Pi. The IP address is shown on completion of boot
10. Download and install PuTTY on your windows machine https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
11. Type PuTTY into the Windows search bar and run the program
12. In the Session category, type in the IP address in the text box labeled Host Name(or IP address)
13. If this is the first time connecting, PuTTY will issue a security alert. Click Yes.
14. Enter pi as the login
15. Enter raspberry as the password

# Connecting to the Raspberry Pi

# Installing Software

# Running Position Detection

# Running Object Recognition Example

# Retraining Object Recognition
