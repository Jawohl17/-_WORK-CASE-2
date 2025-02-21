Install QEMU:
On Ubuntu or Debian:

sudo apt update
sudo apt install qemu qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
On Fedora:

sudo dnf install qemu-kvm libvirt virt-install
Basic Operations in QEMU
1. Creating a New Virtual Machine
To create a new virtual machine, you can use the qemu-system-x86_64 command (for 64-bit systems). For example:

qemu-system-x86_64 -m 2048 -hda /path/to/your/disk.img -cdrom /path/to/your/iso -boot d
-m 2048 - allocates 2048 MB of RAM.
-hda - specifies the hard disk (create it in advance using qemu-img).
-cdrom - specifies the ISO image of the operating system.
-boot d - boots from the CD-ROM.
2. Selecting/Adding Available Hardware for the Virtual Machine
To add additional devices, such as network adapters, you can use command-line options:

-net nic -net user
This will create a virtual network adapter.
3. Configuring Network and Connecting to Wi-Fi Points
To connect to Wi-Fi, you need to set up a network bridge on your host system. This can be done using brctl or nmcli (NetworkManager).
After setting up the bridge, you can connect the virtual machine to it:

-netdev bridge,id=net0,br=br0 -device virtio-net-pci,netdev=net0
4. Working with External Storage Devices (USB Flash Drives)
To connect a USB device to the virtual machine, use the -usb and -device usb-host options:

-usb -device usb-host,hostbus=1,hostaddr=2
Replace hostbus and hostaddr with the appropriate values for your USB device, which can be found using the lsusb command.
Installing a GNU/Linux Operating System
Installing a GNU/Linux Distro:
Start the virtual machine with the ISO image as mentioned above and follow the installer instructions.
Creating a Second Virtual Machine
Creating the Second Virtual Machine:

Use a similar command to create a new virtual machine, but without a graphical interface:

qemu-system-x86_64 -m 1024 -hda /path/to/your/minimal_disk.img -cdrom /path/to/minimal_iso -boot d
Installing the GNOME Desktop Environment:

After installing the base system, you can install GNOME:

sudo apt update
sudo apt install ubuntu-desktop
Installing a Second Desktop Environment:

For example, to install XFCE:

sudo apt install xubuntu-desktop
Comparing the Features of GNOME and XFCE
GNOME:

Modern, aesthetically pleasing interface.
Many built-in features, but can be resource-heavy.
More resource-intensive, which may not be suitable for older systems.
XFCE:

Lightweight and fast, suitable for older hardware.
Customizable and efficient, using fewer resources.
Provides a more traditional desktop experience.

screenshots of works:

![1](https://github.com/user-attachments/assets/35b231dc-cfad-4dfe-9ada-05105d6e0b41)
![3](https://github.com/user-attachments/assets/a9873760-18e8-48da-a23a-26d5954ecd3f)
![2](https://github.com/user-attachments/assets/5e897d17-2cba-414b-b9ba-daf1a0281b65)


