# macOS-emulator version 1 (Still In Testing)
Please do not fork unless you have premission from me
New to macOS? Check [the FAQs.](docs/FAQs.md)

## Getting Started
you will need pip installed and developer mode enabled 
## Step 1
Run `jumpstart.bat` to download installation media for macOS (internet required). The default installation uses Catalina, but you can choose which version to get by adding either `--high-sierra`, `--mojave`, or `--catalina`. For example:
```
./jumpstart.sh --mojave
```
> Note: You can skip this if you already have `BaseSystem.img` downloaded. If you have `BaseSystem.dmg`, you will need to convert it with the `dmg2img` tool in tools.

## Step 2
Create an empty hard disk using `qemu-img`, changing the name and size to preference:
```
qemu-img create -f qcow2 MacOS.qcow2 64G
```

and add it to the end of `basic.sh`:
```
    -drive id=SystemDisk,if=none,file=MacOS.qcow2 \
    -device ide-hd,bus=sata.4,drive=SystemDisk \
```
> Note: If you're running on a headless system (such as on Cloud providers), you will need `-nographic` and `-vnc :0 -k en-us` for VNC support.

Then run `basic.sh` to start the machine and install macOS. Remember to partition in Disk Utility first!

## Step 2a (Virtual Machine Manager)
Hasent been ported yet :(

## Step 2b (Headless Systems) Not Tested
If you're using a cloud-based/headless system, you can use `headless.sh` to set up a quick VNC instance. Settings are defined through variables as seen in the following example. VNC will start on port `5900` by default.

HEADLESS=1 MEM=1G CPUS=2 SYSTEM_DISK=MyDisk.qcow2 ./headless.sh
```
Am Not Testing This
## Step 3

You're done!

To fine-tune the system and improve performance, look in the `docs` folder for more information on [adding memory](docs/guide-performance.md), setting up [bridged networking](docs/guide-networking.md), adding [passthrough hardware (for GPUs)](docs/guide-passthrough.md), tweaking [screen resolution](docs/guide-screen-resolution.md), and enabling sound features.
