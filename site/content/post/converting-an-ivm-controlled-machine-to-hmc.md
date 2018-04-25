---
title: Converting an IVM controlled machine to HMC
date: 2018-04-23T21:49:23.808Z
description: Migrating from IVM to HMC was easier that I had expected.
---
I have a client that wanted to connect their P720 running standalone IVM to an HMC running one of the later releases. There is a lot of great information related to accomplishing this, from reading them it appears that the process was a bit more difficult in the past. 

The one thing that was absolutely clear was the need for backups prior to starting the process. I created a mksysb backup using backupios, copied off a profile backup to my workstation, and created a file with the results of the commands `lsmap -all` `lsmap -all -net` and `lsmap -all -npiv` 

Now that I have everything backed up and copies of critical configurations, it was time to go for it. 

The client had created a private VLAN for us to use for the HMC connections. We decided the best approach was to use the HMC2 connection on the P720 while maintaining access to the ASMI via HMC1. We configured HMC2 for DHCP and ent1 on the HMC to act as a DHCP server, connected the cables and crossed our fingers.

The HMC picked it up right away, and after setting a new password in the HMC for the new server connection, we were able to manage the P720 from the HMC. I was also pleasantly surprised to find that I was still able to connect to the VIO server via SSH and run `mkvt -id LPARID` I was under the impression that I would have to start using just the HMC.

I found the process to be pretty painless, although that could be because we arranged a 24-hour outage window and were fully prepared to reset the FSP and rebuild profiles, VLANs, SEAs and whatever else it took for as long as it took. I am left to wonder if the process would have been as easy had I not prepared much at all. 

I have a new system on order for my lab along with an HMC. I am going to see what it takes to recover from a failed attempt to convert an IVM to HMC managed. Those notes will appear in a later post.

Thank you for reading, if you have any questions drop me a line at rcox@unixandmore.com



Raymond Cox
