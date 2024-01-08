* **Serial Driver**

A package which which encapsulates basic receiving and sending of serial data.

Provided within this package is the following executabe:
- serial_bridge: combined both receiver and sender nodes into one

Provided within this package also is a `serial_driver` library without the ROS2 dependencies which could be used elsewhere.

## Launch Instructions (for MANA use)
```
ros2 launch serial_driver mana_serial_bridge_node.launch.py
```

Params can are set in serial_driver/prams/mana.params.yaml

## Common Issues

### Error creating serial port: /dev/ttyACM0 - open: Permission denied

Cause: You might have missing permissions to access the serial port

Fix: 

1. Add your user account to the dialout group to get permission

    ```
    sudo usermod -a $USER -G dialout
    ```
2. Logout and login again

### If still not able to access serial port (blocking service)

Cause: There is an background process for braille interfaces running on Ubuntu 22.04 by default, that reads from and thus blocks the serial port. It can be uninstalled as follows.

Fix:

1. Remove brltty

```
sudo apt remove brltty
```
### Failed uploading: uploading error: exit status 1
Cause: You might have selected the wrong bootloader for your Arduino processor

Fix:

1. Inside the Arduino IDE navigate to Tools/Processor
2. Choose the correct bootloader

Tipp: Most of the cheap Arduino alternatives use the *"old bootloader"*