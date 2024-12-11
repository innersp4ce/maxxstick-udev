# maxxstick-udev

Udev rule for MaxxStick S3/P3

## Description

The MaxxStick is a niche gamepad device intended to be used with a computer keyboard. The udev rule with installation instructions are meant to make this usable within (Arch) Linux.
MaxxStick was kind enough to help me with this. An unknown user had reported back to them how it was solved on Ubuntu. I have replicated this for Arch.

## Installation

1. Add your user to the uucp group to give read/write acces to serial port.

These groups have rw acces to the serialports the MaxxStick is on. This is needed to use the MaxxUtility.

```
# chmod -aG uucp <user>
# chmod -aG dialout <user>
```
2. Log out to apply group to username.

Chromium/Chrome is required for step 3:

3. Go to [MaxxUtility](https://maxxstick.com/MaxxUtility/)
4. Click connect and select the MaxxStick on `tty*`
5. Click settings
6. Slide Expose DirectInput to on
7. Click Classic Games (DirectInput)

7. Clone repo and copy the udev rule to the correct directory. Reload rules.
```
$ git clone https/github.com/innersp4ce/maxxstick-udev.git
$ cd maxxstick-udev/
# cp maxxstick-udev.rules /usr/lib/udev/rules.d/
# udevadm control --reload
```

## Tips
- Optionally reboot the system. I had issues with my Arch system not appyling the udev rules and groups to the user as well.
- I had issues with reloading the udev rules and the kernel nog recognizing the device anymore. Replugging into a different USB-port solves this issue.
