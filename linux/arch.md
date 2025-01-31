# Arch

Here's a small documentation to mange yourself trough Arch Linux! 😀

> **NOTE**: I mostly use CLI[^1] apps, to manage my system.

## Arch install

If you want to backup or load your config for `archinstall` here are some useful commands you need to know

```bash
# first we need to identify the usb that we will store the configuration onto
lsblk
# then we need to mount the drive before
mkdir -p /mnt/usb && mount /dev/sdaX /mnt/usb;
# restore the saved config (fresh install)
mkdir -p /mnt/usb && mount /dev/sda1 /mnt/usb && archinstall --config /mnt/usb/user_configuration.json --creds /mnt/usb/user_credentials.json;
```

## Manage network

```bash
# Enter into the command line tool
iwctl
# Show available sations (network cards)
station list
# Scan available networks
station wlan0 scan
station wlan0 get-networks
# Connect to scanned network
station wlan0 connect NET_ID
```

## Manage Bluetooth

```bash
# Manage bluetooth
bluetoothctl
# Scan near devices
scan on
# Pairing and connecting
pair XX:XX:XX:XX:XX:XX
trust XX:XX:XX:XX:XX:XX
connect XX:XX:XX:XX:XX:XX
```

## Manage audio

```
# see useful information, like if you are using pipewire or pulseaudio, etc
pactl info
# list all available outputs
pactl list short sinks
# set the output
pactl set-default-sink [number]
```

### Fix audio

Some weird devices like the apple AirPods, don't connect right away you need to modify a file to make them work.

```bash
# uncomment this line at: /etc/bluetooth/main.conf
ControllerMode=dual
```

## Wayland

### Screen sharing

Wayland is a bit fucking weird, and you need to install some extra stuff to make screensharing work on firefox.

```bash
# source https://wiki.archlinux.org/title/XDG_Desktop_Portal
sudo pacman -S xdg-desktop-portal-wlr xdg-desktop-portal-gtk
```


[^1]: Command line interface applications
