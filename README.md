# batterylifenotify

This repository contains the timer I use to notify me when my laptop battery is less than 40 and the charger unplugged or more than 80 and the charger plugged in.  

I have copied some of it off of random sources and edited it as per my needs - for an Arch system running `dwm` and using `notify-send`.  

You may have to do the same if you plan on using it.  

## Requirements
- Systemd
- A utilty to show notifications
- A way to find out the capacity and status of your battery.

## Configuration and customization

**TL;DR** do it manually - edit `batterylifenotify`

You may edit the file `batterylifenotify` to make it fit your system,  
Some things you might want to configure are:
- if your battery info is in other files
- you want to use another command to find out the capacity or the status
- You use a utility other than `notify-send` for your notifications

Or you may want to customise
- the messages you get as notification
- make it notify if the battery level is below 30 instead of 40
- literally anything else - it's all in the file `batterylifenotify`.

## Usage and installation
I plan to write a small script for this in the near future. For now you have:
### Manual
- Copy the `*.timer` and `*.service` file to `~/.config/systemd/user/` i.e. the path where you keep your user level units.  
See note below why we are putting it in the user level and not in /etc/systemd/..
- Copy the file `batterylifenotify` to `/usr/bin`
- Enable and start the timer
```
systemctl --user enable batterylifenotify.timer
systemctl --user start batterylifenotify.timer
```
Note that we're starting it on user level. This is required since notify-send utility requires access to some variables which will be available for a user level daemon.
# Contribute
Issues and PRs are welcome.
