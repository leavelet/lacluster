# LACluster

## Description

A bunch of scripts to run a cluster on top of QEMU. Very naive. Don't use it for anything serious.

## File layout 

All the paths it uses are hardcoded, so you need to have the following layout:

(see `lapath`)

```bash
STATE_FILE=$HOME/qemu/state/list
LOCK_FILE=$HOME/qemu/state/lock
PROFILE_DIR=$HOME/qemu/profiles
BASE_IMAGE_DIR=$HOME/qemu/images/base
CHANGE_IMAGE_DIR=$HOME/qemu/images/change
MONITOR_DIR=$HOME/qemu/monitor
BIOS_DIR=$HOME/qemu/bios
```

## Profile

A profile is used for creating a new VM. It's a simple text file with the following format:

```bash
QEMU_BIN=qemu-system-loongarch64
MEM=16G
CPU=la464-loongarch-cpu
MACHINE=virt
SMP=4
BIOS=loongarch-qemu-uefi.fd
```

It will find the base image in `BASE_IMAGE_DIR` and the change image in `CHANGE_IMAGE_DIR`. The change image is a qcow2 image that will be used to store the changes made to the base image.

## Usage

```bash
lacluster profile base number
lastate name
lapower name on|off
```

Where `profile` is the name of the profile, `base` is the name of the base image and `number` is the number of VMs to create.
