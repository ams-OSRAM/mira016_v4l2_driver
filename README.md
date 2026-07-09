# ams-mira016 Linux driver

## Installation

### Driver

Compile the driver using the Makefile

```
make
```

Place it in the kernel modules folder.

```
sudo mkdir -p /lib/modules/$(uname -r)/updates && sudo cp mira050.ko /lib/modules/$(uname -r)/updates/
```

Resolve modules dependencies.

```
sudo depmod -a
```

### Device tree

Compile the device tree overlay matching your platform and plugin board from the `dts` folder.

```
cd dts/rpi
sudo dtc mira016-overlay.dts -o /boot/firmware/overlays/mira016.dtbo
```

Set the device tree overlay in your platform. This may differ from platform to platform. Please refer to your platform documentation.

This is how to set the device tree overlay for Raspberry Pi.

```
echo "dtoverlay=mira016" | sudo tee -a /boot/firmware/config.txt
```

Finally, run `sudo reboot` to test your changes.

