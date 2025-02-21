**Work-case 2**
Installation of Hypervisor

Choosing a Hypervisor

I opted for QEMU due to its flexibility and support for various architectures. It was aimed at updating "VirtualBox" drivers.

Basic Actions in QEMU

**1. Creating a New Virtual Machine**

Installing QEMU

If QEMU is not installed, use the following command based on your distribution:

sudo apt update
sudo apt install qemu qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils

Creating a Disk Image

qemu-img create -f qcow2 my_vm_image.qcow2 20G

Launching the Virtual Machine

qemu-system-x86_64 -hda my_vm_image.qcow2 -boot d -cdrom path_to_your_iso.iso -m 2048

Replace path_to_your_iso.iso with the actual path to your ISO image.

**2. Selecting/Adding Available Hardware**

Configure CPU and RAM

qemu-system-x86_64 -hda my_vm_image.qcow2 -m 2048 -smp 2

Add Network Interface

-netdev user,id=mynet0 -device e1000,netdev=mynet0

**3. Configuring Network and Connecting to Wi-Fi**

Bridged Networking

To connect to a Wi-Fi network, you can configure a bridged network:

-netdev tap,ifname=tap0,script=no,downscript=no,id=mynet0 -device e1000,netdev=mynet0

Ensure the tap interface is created and configured properly.

**4. Working with External Storage Devices**

Access USB Devices

-usb -device usb-host,hostbus=1,hostaddr=2

Find hostbus and hostaddr values using:

lsusb

Installing a GNU/Linux Operating System

**1. Installing a GNU/Linux Distribution**

Start the VM using the above commands with an ISO image.

Follow the installation steps to complete the process.

Creating a Second Virtual Machine

**1. Installing a Minimal Configuration**

Creating a New Disk Image

qemu-img create -f qcow2 my_vm_image_minimal.qcow2 20G

Launching Minimal VM

qemu-system-x86_64 -hda my_vm_image_minimal.qcow2 -boot d -cdrom path_to_minimal_iso.iso -m 2048

Installing the Base System (Without GUI)

Follow the minimal installation steps and complete the setup.

**2. Installing the GNOME Desktop Environment**

sudo apt update
sudo apt install ubuntu-desktop

Reboot the system after installation.

**3. Installing a Second Desktop Environment (XFCE)**

sudo apt install xubuntu-desktop

Reboot after installation to apply changes.

Comparing GNOME and XFCE

**GNOME**

Interface: Modern and polished.

Customization: Supports extensions but requires more setup.

Performance: Higher resource usage.

**XFCE**

Interface: Lightweight and traditional.

Customization: Easily customizable with themes and plugins.

Performance: Lower resource consumption, ideal for older systems.


![1](https://github.com/user-attachments/assets/35b231dc-cfad-4dfe-9ada-05105d6e0b41)
![3](https://github.com/user-attachments/assets/a9873760-18e8-48da-a23a-26d5954ecd3f)
![2](https://github.com/user-attachments/assets/5e897d17-2cba-414b-b9ba-daf1a0281b65)

**Conclusion**

GNOME provides a sleek, modern experience but requires more system resources. XFCE, on the other hand, is lightweight and customizable, making it an excellent choice for performance-focused users.


