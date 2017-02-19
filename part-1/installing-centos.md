---
recipe: Installing OVS on CentOS 7
section: Installation
author: Scott S. Lowe
---

# Installing OVS on CentOS 7

## Problem

You have a CentOS 7-based system on which you'd like to install OVS.

## Solution

To install OVS on a CentOS 7 system, you must enable some additional repositories that offer OVS packages. Once the additional repositories are enabled, you can install OVS using `yum`.

While this greatly simplifies the process of installing OVS onto a CentOS-based system, it does mean that you may have to trade off having the most recent version of OVS in exchange for convenience. The versions of OVS that are available via the repositories often lag somewhat behind the released versions of OVS. To get a more recent version, you'll have to [install OVS from source](part-1/compiling-from-master.md).

## Details

By default, OVS packages are not available in any of the standard repositories enabled in a typical CentOS 7 installation. In order to install OVS on CentOS 7 using `yum`, you'll need to first enable some additional repositories. Specifically, you'll need to enable some OpenStack-related repositories using the following command (if you're not root, you'll need to preface this command---and all other commands in this recipe---with `sudo`):

    yum install centos-release-openstack-newton

As of this writing, this was the most recent version of this repository. However, as OpenStack releases continue, this repository would be updated to reflect new OpenStack releases as well. Therefore, in the future, the name of this repository would likely be different.

This will, in turn, enable the following package repositories:

* centos-release-ceph-jewel
* centos-release-virt-common
* centos-release-qemu-ev
* centos-release-storage-common
* centos-release-openstack-newton

You can verify that the additional repositories are installed and enabled using `yum repolist`.

Once these repositories are enabled, you can install OVS using this command:

    yum install openvswitch

If you are using the "centos-release-openstack-newton" repositories, this will install version 2.5.0 of OVS.

After OVS is installed, run `systemctl enable openvswitch` to tell systemd to start the OVS services automatically. You can then reboot the system, or run `systemctl start openvswitch` to manually start OVS.

## Additional Information

_TODO_
