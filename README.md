# jetson-flash in Poly Perception

For now, it only supports jetson-agx-orin board with auvidea carrier board (ref : X230D). 
It allows to use auvidea I/O with balena OS and Jetson Linux 35.3.1 which support Deepstream 6.2.

## How to flash
### 1. Reset mode 
Power off the board
Connect the board to the Linux host PC. Please use a USB 2.0 cable (micro-USB on the carrier board).
Connect the boar to power. As linked to the Linux host PC through usb 2.0 cable, board goes automatically into recovery mode. 

Check that the board is detected by the host PC : 

```sh
$ lsusb
> ...
> Bus 003 Device 007: ID 8087:0026 Nvidia Corp.
> ...
```

### 2. Flash 
- Download balena os image and jetson linux BSP filled with Auvidea requirements : 

```sh
$ dvc pull
```
tar files are located in `./images/` folder.

- Download balena image from balena cloud :
Later in the Readme, the location of the balena image is defined as `<path/to/balena_os.img>`

- install dependencies : 

```sh
$ npm install
```
(Conflicts can occur but during my personnal experience, it didn't impact the flashing process)

- Run node.js script : 

```sh
./bin/cmd.js -f <path/to/balena_os.img> -p -o ./ -m jetson-agx-orin-devkit
```

The flashing process may take 5 - 15 minutes or longer during which a lot of log output will appear. If all goes well, you'll see something similar to the following upon completion:

```
*** The target t186ref has been flashed successfully. ***
Reset the board to boot from internal eMMC.
```


License
-------

Fork from balena-os/jetson-flash

The project is licensed under the Apache 2.0 license.
