---
title: Converting an IVM controlled machine to HMC
date: 2018-04-23T21:49:23.808Z
description: Migrating from IVM to HMC controlled used to be complicated.
---
The process boils down to:

1. Create a new backupios mksysb image
2. Save off a copy of the profile data.
3. Stop all LPARs except the VIO. \*\*Not sure this is absolutely necessary\*\*
4. Make sure the FSP is set to DHCP and connect to the HMC
5. Set new system to HMC credentials
6. Some of the documentation indicates the profiles will need to be saved, that was not my experience. All profiles came across with no problems.
