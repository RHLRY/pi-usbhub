# usbipHUB
source credit from [this page](https://github.com/cezanne/usbip-win/blob/master/README.md) 

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

## Client Side (Windows x64)

### Instuctions

  - find all files in output folder after build or on [release](https://github.com/cezanne/usbip-win/releases) page. I've also shared usbip-win 0.3.5 on this repo.
  - Unzip it
  - select usbip_test.pfx file and install like bellow ((password: usbip))
    1. double click -> select loacal machine -> choose Yes(Admin Promt) -> give password (usbip), everything as is -> select place all certificate in following store & select "Trusted Root Certification Authority"
    2. double click -> select loacal machine -> choose Yes(Admin Promt) -> give password (usbip), everything as is -> select place all certificate in following store & select "Trusted Publishers"

powershell commands -> Run PowerShell or CMD as an Administrator to enable test signing

  `> bcdedit.exe /set TESTSIGNING ON`

Restart System

powershell commands -> Run PowerShell or CMD as an Administrator

    - PS> cd [to extract location]
    - PS> usbip.exe install
    - .\usbip.exe list -r [ip address of raspberry pi] PS> .\usbip.exe list -r 192.168.1.18

output
```
    Intel Corp.
Exportable USB devices
======================
 - 192.168.1.18
      1-1.3: DragonRise Inc. : PC TWIN SHOCK Gamepad (0079:0006)
           : /sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3
           : (Defined at Interface level) (00/00/00)
``` 

    - .\usbip.exe attach -r 192.168.1.18 -b 1-1.3
           
output
```
succesfully attached to port 0
```
powershell commands -> Run PowerShell or CMD as an Administrator -> to get port number

    .\usbip.exe port
    .\usbip.exe detach -p 0
    
output
```
port 0 is succesfully detached
```
        
















