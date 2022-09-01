# macOS-emulator version 1 (Still In Testing)
This A Fork For macos-simple-kvm (https://github.com/foxlet/macOS-Simple-KVM)
New to macOS? Check [the FAQs.](docs/FAQs.md)

## Getting Started
You Will Need WSL UBUNTU, DEBAIN on from the microsoft store
Then open
```
install.cmd
```
## Step 1
open download (os ver) to download installation media for macOS (internet required).I have made it user-friendly (who wants to use a command promt) 
```
jumpstart-mojave.cmd
```
> Note: You can skip this if you already have `BaseSystem.img` downloaded. If you have `BaseSystem.dmg`, you will need to convert it with the `dmg2img` tool in tools.

## Step 2
Create an empty hard disk using `qemu-img` ,to change the size edit the file ,if you change the name it may not work
```
qemu-ing.cmd
```
> Note: If you're running on a headless system (such as on Cloud providers), you will need `-nographic` and `-vnc :0 -k en-us` for VNC support.

Then run `basic.cmd` to start the machine and install macOS. Remember to partition in Disk Utility first!

## Step 2a (Virtual Machine Manager)
Hasent been ported yet :(

## Step 2b (Headless Systems) Not Tested
If you're using a cloud-based/headless system, you can use `headless.sh` to set up a quick VNC instance. Settings are defined through variables as seen in the following example. VNC will start on port `5900` by default.
```
HEADLESS=1 MEM=1G CPUS=2 SYSTEM_DISK=MyDisk.qcow2 ./headless.sh
```
Am Not Testing This
## Step 3

You're done!

To fine-tune the system and improve performance, look in the `docs` folder for more information on [adding memory](docs/guide-performance.md), setting up [bridged networking](docs/guide-networking.md), adding [passthrough hardware (for GPUs)](docs/guide-passthrough.md), tweaking [screen resolution](docs/guide-screen-resolution.md), and enabling sound features.
