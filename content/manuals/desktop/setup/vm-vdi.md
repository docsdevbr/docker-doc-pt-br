---
# Copyright (c) 2016 Docker, Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

description: Instructions on how to enable nested virtualization
keywords: nested virtualization, Docker Desktop, windows, VM, VDI environment
title: Run Docker Desktop for Windows in a VM or VDI environment
aliases:
 - /desktop/nested-virtualization/
 - /desktop/vm-vdi/
weight: 30
---
In general, we recommend running Docker Desktop natively on either Mac, Linux, or Windows. However, Docker Desktop for Windows can run inside a virtual desktop provided the virtual desktop is properly configured. 

To run Docker Desktop in a virtual desktop environment, it is essential nested virtualization is enabled on the virtual machine that provides the virtual desktop. This is because, under the hood, Docker Desktop is using a Linux VM in which it runs Docker Engine and the containers.

## Virtual desktop support

> [!NOTE]
>
> Support for running Docker Desktop on a virtual desktop is available to Docker Business customers, on VMware ESXi or Azure VMs only.

The support available from Docker extends to installing and running Docker Desktop inside the VM, once the nested virtualization is set up correctly. The only hypervisors we have successfully tested are VMware ESXi and Azure, and there is no support for other VMs. For more information on Docker Desktop support, see [Get support](/manuals/desktop/troubleshoot-and-support/support.md).

For troubleshooting problems and intermittent failures that are outside of Docker's control, you should contact your hypervisor vendor. Each hypervisor vendor offers different levels of support. For example, Microsoft supports running nested Hyper-V both on-prem and on Azure, with some version constraints. This may not be the case for VMWare ESXi.

Docker does not support running multiples instances of Docker Desktop on the same machine in a VM or VDI environment. 

## Turn on nested virtualization

You must turn on nested virtualization before you install Docker Desktop on a virtual machine.

### Turn on nested virtualization on VMware ESXi

Nested virtualization of other hypervisors like Hyper-V inside a vSphere VM [is not a supported scenario](https://kb.vmware.com/s/article/2009916). However, running Hyper-V VM in a VMware ESXi VM is technically possible and, depending on the version, ESXi includes hardware-assisted virtualization as a supported feature. For internal testing, we used a VM that had 1 CPU with 4 cores and 12GB of memory.

For steps on how to expose hardware-assisted virtualization to the guest OS, [see VMware's documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-2A98801C-68E8-47AF-99ED-00C63E4857F6.html).


### Turn on nested virtualization on an Azure Virtual Machine

Nested virtualization is supported by Microsoft for running Hyper-V inside an Azure VM.

For Azure virtual machines, [check that the VM size chosen supports nested virtualization](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes). Microsoft provides [a helpful list on Azure VM sizes](https://docs.microsoft.com/en-us/azure/virtual-machines/acu) and highlights the sizes that currently support nested virtualization. For internal testing, we used D4s_v5 machines. We recommend this specification or above for optimal performance of Docker Desktop.

## Docker Desktop support on Nutanix-powered VDI

Docker Desktop can be used within Nutanix-powered VDI environments provided that the underlying Windows environment supports WSL 2 or Windows container mode. Since Nutanix officially supports WSL 2, Docker Desktop should function as expected, as long as WSL 2 operates correctly within the VDI environment.

If using Windows container mode, confirm that the Nutanix environment supports Hyper-V or alternative Windows container backends.

### Supported configurations

Docker Desktop follows the VDI support definitions outlined [previously](#virtual-desktop-support):

 - Persistent VDI environments (Supported): You receive the same virtual desktop instance across sessions, preserving installed software and configurations.

 - Non-persistent VDI environments (Not supported): Docker Desktop does not support environments where the OS resets between sessions, requiring re-installation or reconfiguration each time. 

### Support scope and responsibilities

If WSL 2 encounters issues - for example, it crashes, fails to start, or experiences performance degradation - contact Nutanix support.

If Docker Desktop itself encounters issues, contact Docker support.
