
Step 4 — Assign the two interfaces

After reboot, you'll get the OPNsense console.

You should see something similar to:

WAN -> DHCP
LAN -> 192.168.1.1/24

Don't assume the interface names are em0 and em1.

Your VMware virtual NICs may have different names.

Choose:

1) Assign interfaces

OPNsense's console specifically provides this interface-assignment option.

For now:

WAN = VMware NAT adapter
LAN = VMware VMnet10 adapter

The important thing is the physical/virtual adapter, not the name.

Step 5 — Give the LAN temporary management IP

From the OPNsense console select:

2) Set interface(s) IP address

Choose:

LAN

Set:

IPv4 address: 10.10.99.1
Prefix: 24

So:

LAN = 10.10.99.1/24

For DHCP, we can temporarily enable it if needed, but we'll properly configure DHCP after the VLANs are created.
