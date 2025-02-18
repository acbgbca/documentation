# Server Setup

## Add Partition

Easiest to do with Cockpit:
* Go to storage
* Select unallocated disk space, and create a Partition
* Create a new partition:
  * Name: Temp
  * Mount point: /tmp
  * Type: ext4 (or similar)
  * Mount before services

## Install nVidia Driver

[Ubuntu Instructions](https://ubuntu.com/server/docs/nvidia-drivers-installation)

* Log onto server
* Install Driver: `sudo ubuntu-drivers install`

