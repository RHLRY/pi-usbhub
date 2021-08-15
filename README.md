# usbipHUB

## Server Side (Linux Distro-> raspberry pi)
### commands
    sudo apt update
    sudo apt install usbip
    sudo modprobe vhci-hcd
    sudo modprobe usbip-host
    sudo usbip list -l
output
```
 - busid 1-1.3 (0079:0006)
   DragonRise Inc. : PC TWIN SHOCK Gamepad (0079:0006)
```
### commands
    sudo usbip bind -b 1-1.3
output
```
usbip: info: bind device on busid 1-1.3: complete
```
### commands
    sudo usbip unbind -b 1-1.3
output
```
usbip: info: unbind device on busid 1-1.3: complete
```
### commands
    sudo usbipd
output
```
usbipd: info: starting usbipd (usbip-utils 2.0)
usbipd: info: listening on 0.0.0.0:3240
usbipd: info: listening on :::3240
```

















