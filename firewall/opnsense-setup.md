
— Install OPNsense

If you already created the OPNsense-FW VM, start it with the OPNsense ISO attached.

OPNsense officially supports installation from the DVD ISO in a virtual machine. The current documentation recommends at least 3 GB RAM; your 4 GB allocation is appropriate for this lab.

1. Boot the VM

You should eventually see an OPNsense console/login screen.

At the login prompt, use:

Username: installer
Password: opnsense

The official installation documentation confirms these credentials for starting the installer.

2. Installation choices

When the installer starts:

Keymap

Choose:

Continue with default keymap

Then choose:

Install (ZFS)

For our VM with a single virtual disk, use the default stripe option.

Select your 30 GB virtual disk.

⚠️ Make absolutely sure you're selecting the OPNsense VM's virtual disk. The installation will erase the selected disk.

3. Root password

Set a new password.

Don't use:

opnsense

Create your own strong lab password.

Then:

Complete Install

Reboot.

4. Remove the ISO

After the VM shuts down/reboots:

VM → Settings → CD/DVD

Either:

Use physical drive

or preferably:

Disconnect

so the VM boots from its virtual disk.

