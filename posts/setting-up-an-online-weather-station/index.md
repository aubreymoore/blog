<!--
.. title: Setting Up an Online Weather Station
.. slug: setting-up-an-online-weather-station
.. date: 2017-04-09 02:43:59 UTC+10:00
.. tags: Raspberry Pi
.. category:
.. link:
.. description:
.. type: text
-->

Was asked to set up an on-line weather station for the University of Guam's Agricutural Experiment Station at Yigo, Guam. The weather station is a [Davis Vantage Pro 2 Plus](http://www.davisnet.com/solution/vantage-pro2/) on a mast mounted on the roof of a 40 foot shipping container. The container is equipped with internet access via a cable modem. Data is fetched from the weather instruments using a Davis Vantage Pro 2 console fitted with an optional data logger.

Decided to use a [Raspberry Pi 3](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) to read data from the weather station console via USB. Data is stored using [weewx](http://www.weewx.com/) software, which also takes care of sending it to Weather Underground. The RP is connected to the modem by a cable.

## Step 1: Install weewx on RPi

## Step 2: Remove the Fake Clock on the RPi

Following the suggestion in
<https://github.com/weewx/weewx/wiki/Raspberry-Pi>,
I deleted the fake hardware clock from the RPi:

    $ sudo apt-get purge fake-hwclock

This forces **weewx** to wait until a software clock is set from the internet connection before resuming after a power outage.

## Step 3: Create a Weather Underground Personal Weather Station and Configure weewx to Feed It

Followed these directions:
<https://publiclab.org/notes/amysoyka/06-20-2014/how-to-set-up-your-weather-station-and-stream-it-to-the-internet>

WU assigned **KYIGO4** as the weather station ID.


## Step 4: Access Weather Station Online

The weather station is online at:
<https://www.wunderground.com/personal-weather-station/dashboard?ID=KYIGO4>

This page automatically updates every few seconds.

<a href="http://www.wunderground.com/weatherstation/WXDailyHistory.asp?ID=KYIGO4"><img src="http://banners.wunderground.com/cgi-bin/banner/ban/wxBanner?bannertype=pws250&weatherstationcount=KYIGO4" width="250" height="150" border="0" alt="Weather Underground PWS KYIGO4" /></a>

## Notes

All outdoor sensors were replaced on April 21, 2017 because the temperature/humidity senor was not working.
