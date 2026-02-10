# Task 2 - Linux Architecture, Processes, and systemd

## Tasks
*  The core components of Linux (kernel, user space, init/systemd)
*  How processes are created and managed
*  What systemd does and why it matters
*  Explain process states (running, sleeping, zombie, etc.)
*  List 5 commands you would use daily


### This is the one shot map that tells everything.   
If I say about classic linux then I should say: `User Space` -> `Kernel Space` -> `Firmware` -> `Hardware`
```
┌──────────────────────────────┐
│ User Applications            │
│ (htop, vim, firefox, bash)   │
│ Troubleshoot:                │
│  - htop/top                  │
│  - ps aux / ps -ef           │
│  - strace                    │
│  - lsof                      │
│  - journalctl (app logs)     │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ Services                     │
│ (nginx.service, sshd.service)│
│ Troubleshoot:                │
│  - systemctl status <service>│
│  - journalctl -u <service>   │
│  - ps/htop                   │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ System Processes             │
│ (systemd, getty, logind)     │
│ Troubleshoot:                │
│  - journalctl                │
│  - ps/htop                   │
│  - systemctl --failed        │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ Kernel Threads               │
│ (kworker/*, ksoftirqd/*)     │
│ Troubleshoot:                │
│  - dmesg                     │
│  - /proc                     │
│  - perf/ftrace/bpftrace      │
│  - iotop/vmstat/mpstat       │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ Kernel                       │
│ (manages CPU, memory, drivers)│
│ Troubleshoot:                │
│  - dmesg                     │
│  - lsmod/modinfo             │
│  - /proc                     │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ Bootloader/Firmware          │
│ (GRUB/UEFI)                  │
│ Troubleshoot:                │
│  - Boot logs                 │
│  - firmware diagnostics      │
└───────────────┬──────────────┘
                │
┌───────────────▼──────────────┐
│ Hardware                     │
│ (CPU, RAM, Storage, NIC, GPU)│
│ Troubleshoot:                │
│  - Memtest86                 │
│  - SMART/hdparm              │
│  - lspci/lsusb/sensors       │
└──────────────────────────────┘
```

### Core Component of Linux (Kernel, User Space & Systemd)
Actually they are core component of Linux such as Kernel Space and User Space. Systemd is part of User Space which is the manager who manages services, processes. Keep in mind I said processes not system processes. On map as you see services, system processes & applications all are into the User Space.

### How processes are created and managed
It depend what type of processes are you talking about. There two types of processes one is system processes another is simple processes. System processes are created by Kernel and other process like you did on shell like htop then htop talks to library called glibc which called appropriate function then it translate into system call to talk with kernel. If everythings goes well kernel says hey its okey you can have access the messenger glibc tell here you go what you wanted. This is how the process is created. Now, a user can see interactive information via htop application.

### What systemd does and why it matters
Simply a manager who manages processes. systemd is not creator of process cause it create something you have to talk with kernel.

### Explain process states (running, sleeping, zombie, etc.)
This is interesting topic. You created processes are there managing by the manager now you also need to know that should you need to take any action or just leave as it is? Let's find it out.
