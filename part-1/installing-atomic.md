---
recipe: Installing OVS on CentOS Atomic Host
section: Installation
author: Scott S. Lowe
---

# Recipe 1.5: Installing OVS on CentOS Atomic Host

## Problem

You have one or more systems running CentOS Atomic Host (version 7.20160818 or later) onto which you'd like to install OVS.

This process should also work for Fedora Atomic Host-based systems.

## Solution

CentOS Atomic Host is unlike most other Linux distributions in that you don't traditionally install packages using a package manager. However, in version 7.20160818, the CentOS Atomic Host added support for something called _package layering_, which allows administrators to add packages to the base build of Atomic Host. Using package layering, it's possible to install OVS onto a CentOS Atomic Host-based system.

## Details

To utilize package layering in order to install OVS on an Atomic Host, you'll need to use the `rpm-ostree` command.

First, you'll need to layer in the latest OpenStack repository, which includes the packages for OVS (as described in Recipe 1.4):

    rpm-ostree pkg-add centos-release-openstack-newton

You'll need to reboot after enabling the repository; proceeding to the next step won't work.

Once you've rebooted the system after the OpenStack repository is enabled, then you can layer in the OVS package:

    rpm-ostree pkg-add openvswitch

Once OVS is layered in, you'll need to reboot before you can use `systemctl` to enable the OVS services. Once you've rebooted, you can use `systemctl enable openvswitch` to tell the Atomic Host to start OVS on boot, and `systemctl start openvswitch` to start OVS and its components.

## Additional Information

More information about the package layering support for CentOS Atomic Host is described in [this blog post](http://www.projectatomic.io/blog/2016/08/new-centos-atomic-host-with-package-layering-support/).
