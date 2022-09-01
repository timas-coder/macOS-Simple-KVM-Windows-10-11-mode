# macOS-Simple-KVM


## Getting Started
Ubuntu wsl version installed 
Then run
```
install.cmd
```
## Step 1 you can skip this step if you have basesystem.img installed
Run `download ------.cmd or bat` to download installation media for macOS (internet needed). The default installation uses Catalina, but you can choose which version to get by opening mojave ,highsierra and catalina For example:
```
download mojave.cmd
```

## Step 2
Create an empty hard disk using `qemu-img`, changing the name and size to preference:
```
qemu-img.cmd
```

and add it to the end of `basic.sh`the linux ver
```
    -drive id=SystemDisk,if=none,file=MyDisk.qcow2 \
    -device ide-hd,bus=sata.4,drive=SystemDisk \
```
> Note: If you're running on a headless system (such as on Cloud providers), you will need `-nographic` and `-vnc :0 -k en-us` for VNC support.

Then run `basic.cmd` to start the machine and install macOS. Remember to partition in Disk Utility first!

## Step 2a (Virtual Machine Manager)not inported yet
1. If instead of QEMU, you'd like to import the setup into Virt-Manager for further configuration, just run `sudo ./make.sh --add`.
2. After running the above command, add `MyDisk.qcow2` as storage in the properties of the newly added entry for VM.

## Step 2b (Headless Systems)not imported yet
If you're using a cloud-based/headless system, you can use `headless.sh` to set up a quick VNC instance. Settings are defined through variables as seen in the following example. VNC will start on port `5900` by default.
```
HEADLESS=1 MEM=1G CPUS=2 SYSTEM_DISK=MyDisk.qcow2 ./headless.sh
```

## Step 3

You're done!

To fine-tune the system and improve performance, look in the `docs` folder for more information on [adding memory](docs/guide-performance.md), setting up [bridged networking](docs/guide-networking.md), adding [passthrough hardware (for GPUs)](docs/guide-passthrough.md), tweaking [screen resolution](docs/guide-screen-resolution.md), and enabling sound features.
