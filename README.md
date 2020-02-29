# Android-Linux-Bluetooth-Communication
This repository details the steps to open a RFID communication channel on an Ubuntu PC and receive data from an Android app through Bluetooth.

As I haven't found many complete tutorials that aid with the understanding of how to open communication channels for Bluetooth communication between a Linux PC with an Android app, I decided to summarise the set of steps/commands that would help get anyone up and running easily.

To set up your Linux PC follow through these set of commands
Install bluez:
> sudo apt-get install bluetooth bluez

Ensure your bluetooth services and bluez are enabled and started:
> sudo systemctl enable bluetooth

> sudo systemctl start bluetooth

> sudo service bluetooth status

> sudo nano /lib/systemd/system/bluetooth.service 

(add a -C after ExecStart=/usr/local/libexec/bluetooth/bluetoothd then save and exit)

> pip install pybluez 

Then make sure the Linux device's bluetooth adapter is on, pairable and discoverable using the following commands.
In a terminal type:
> bluetooth_ctl
Then:

> power on

> pairable on

> discoverable

Then pair your Android device and Linux devices

> sudo chmod +x bluetooth_adv
> sudo ./bluetooth_adv

Now everything is set

To open up a communication channel and server run

> sudo python rfcomm_server.py

(Must include sudo to provide admin privileges.)
