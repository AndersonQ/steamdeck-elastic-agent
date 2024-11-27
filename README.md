# steamdeck-sensors-api

A tiny HTTP API for Steam Deck `sensors` to be used to ingest GPU information into Elasticsearch using the Elastic Agent.

## Installation

```shell
go install github.com/AndersonQ/steamdeck-sensor@latest
sudo steamdeck-sensor install
```

Or download the binary from the release page


## Recover the root password

If you lost your Steam Deck root password (of course I did not lose mine):

 - [Steam Deck Recovery Instructions](https://help.steampowered.com/en/faqs/view/1b71-edf2-eb6d-2bb3)
 - make a bootable flash drive:

```shell
bzcat /path/to/steamdeck-repair-image.img.bz2 | sudo dd if=/dev/stdin of=/dev/sdX oflag=sync status=progress bs=128M
```

 - > Shut down your Steam Deck if it isn't already off. Hold 'Volume Down' and click the Power Button - when you hear the chime, let go of the Volume Down button, and you'll be booted into the Boot Manager.

 - `sudo ~/tools/repair_device.sh chroot` should chroot into the installed system, but there is a [bug](https://github.com/ValveSoftware/SteamOS/issues/1428#issuecomment-2039866494). Thus do it manually using relative paths:
```shell
cd /dev
sudo steamos-chroot --disk nvme0n1 --partset A
pass deck # to change the password for the deck user
```