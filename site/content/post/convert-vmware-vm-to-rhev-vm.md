---
title: Convert VMware VM to RHEV VM
date: 2018-06-03T19:11:06.114Z
description: I needed to convert a Windows VM running on ESXi to RHEV without vCenter.
---
I am running ESXi 6.5 on some old hardware and I really only use it to host one Windows VM for use with a specific client. As I have recently started converting to Red Hat Enterprise Virtualization instead of VMware, it seemed like an ideal opportunity to figure out what it would take to convert a VMware VM to a RHEV VM.

I started by using the virt-v2v command to try and connect to the ESXi server and import the VM into my RHEV cluster. Because I do not use vCenter to manage the one ESXi server I have, I was unable to make this work. 

After much testing and reading of documentation, I found the easiest method was to create a single ovf file from the VMware vSphere Client, and then use virt-v2v to import the ovf into an Export domain. You can then load that image into the clusters storage domain.
