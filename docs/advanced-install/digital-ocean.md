# DigitalOcean

> **Warning** -- Most cloud providers have been IP blocked from accessing the API

## Prerequisites

- [A DigitalOcean account](https://m.do.co/c/fb6730f5bb99) - Using this link will grant $10 in credit, enough for running your server for up to 2 months.
- [A Google Maps API key](http://rocketmap.readthedocs.io/en/develop/basic-install/google-maps.html)

## Installation

Create a Droplet in your DigitalOcean control panel with Ubuntu 16.04, any Droplet size will work.

Check the "User Data" box lower on the page and enter the following:

```
#!/bin/bash

apt-get -y update
apt-get -y install python python-pip git
git clone --recursive https://github.com/GlobalPlusPlus/RocketMapPlusPlus.git /root/RocketMapPlusPlus
cd /root/RocketMapPlusPlus
pip install -r requirements.txt
python runserver.py -k [Google Maps API key] -l "[LOCATION]" -H 0.0.0.0 -P 80
```

**Important:** Be sure to replace `[API Key]`, and `[LOCATION]` with your Google Maps API Key, and your location (Latitude and Longitude), respectively. You will be able to change locations later on the site.

Once you have that, create your Droplet. Setup will take a few minutes initially, but once it's done your map will be accessible at `http://[YOURDROPLET]/`, replacing that of course with your Droplet's IP address.

## Starting the server

On the first boot the server will start automatically so this step isn't necessary, however if you have to restart the Droplet for any reason, you can start PoGoMap with the following two commands:

```
cd /root/RocketMapPlusPlus
python runserver.py -k [Google Maps API key] -l "[LOCATION]" -H 0.0.0.0 -P 80
```

Credit: [JonahAragon](https://github.com/JonahAragon)
