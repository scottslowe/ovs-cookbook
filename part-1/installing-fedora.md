---
recipe: Installing OVS on Fedora 23/24/25
section: Installation
author: Scott S. Lowe
---

# Recipe 1.6: Installing OVS on Fedora 23/24/25

## Problem

You'd like to install OVS on a system running Fedora 23, 24, or 25.

## Solution

The default repositories for Fedora 23, 24, and 25 include version 2.5.0 of Open vSwitch, so all that's required to install OVS is to use Fedora's `dnf` utility to install the appropriate packages.

## Details

The default repositories for Fedora 23/24/25 include packages for version 2.5.0 of OVS. To install OVS, just use `dnf` (you'll need to preface this command with `sudo` if you're not running as root):

    dnf install openvswitch

Once the OVS packages are installed, use `systemctl enable openvswitch` to tell systemd to launch the OVS services on boot. Then, either reboot the Fedora system or use `systemctl start openvswitch` to start OVS manually.

## Additional Information

None
