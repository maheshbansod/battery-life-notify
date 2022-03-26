# batterylifenotify

This repository contains the timer I use to notify me when my laptop battery is less than 40 and the charger unplugged or more than 80 and the charger plugged in.

## Requirements
- Systemd
- A utilty to show notifications
- A way to find out the capacity and status of your battery.

## Configuration and customization
The file `config.cfg` can be used to configure it.  
Modify the variables as you see fit.
Currently, it includes the variables
```BELOWFILE
ABOVEFILE
MIN
MAX
BATTERY_DIR
LOW_BATTERY_MESSAGE
HIGH_BATTERY_MESSAGE
```

Feel free to edit the file `batterylifenotify` using which you can use your preferred notification utility if it's other than `notify-send` .

// TODO: maybe edit this after creating the installation script

## Usage and installation
I plan to write a small script for this in the near future. For now you have:
### Manual
- Copy the `*.timer` and `*.service` file to `~/.config/systemd/user/` i.e. the path where you keep your user level units.  
See note below why we are putting it in the user level and not in /etc/systemd/..
- Copy the file `batterylifenotify` to `/usr/bin`
- Copy the configuration file `config.cfg` to `~/.config/batterylifenotify/config.cfg`
- Enable and start the timer
```
systemctl --user enable batterylifenotify.timer
systemctl --user start batterylifenotify.timer
```
Note that we're starting it on user level. This is required since notify-send utility requires access to some variables which will be available for a user level daemon.
# Contribute
Issues and PRs are welcome.
