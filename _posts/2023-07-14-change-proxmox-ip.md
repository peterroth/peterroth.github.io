---
title: Change IP of Proxmox machines
tags: proxmox cluster change
---
I have the luxury to have access to a [Proxmox cluster](https://www.proxmox.com/en/), consisting of 3 machines, forming a quorum. I was able to manage their configuration and the residing virtual machines and containers from one of the machine's web interface, until I moved them from one IP range (10.10.1.0/24) to another (10.10.2.0/24). After this change, I wasn't able to manage the cluster as a whole.  
If you have an enterprise subscription, changing the physical machines' address isn't an issue, but the case is different for free users. Here's the workaround:  
1. Set the machine to local mode:  
`systemctl stop pve-cluster`  
`/usr/bin/pmxcfs -l`
2. Edit the *corosync.conf* file on every machine:  
`vi /etc/pve/corosync.conf`  
Change the ring0_addr value from the previous IP to the current IP on every machine and **increase the config_version** (below totem).  
This things cannot be done without setting the machine to local mode.
3. Edit the *hosts* file on every machine:  
`vi /etc/hosts`  
Change the machine's previous IP to the current one.  
4. Reboot the machines.  
They should come online and you should be able to manage configurations, VMs and containers from one UI.  
  
The solution to be able to edit the corosync.conf file was shared on [austinsnerdythings.com](https://austinsnerdythings.com/2021/04/05/proxmox-cluster-manual-update/).
