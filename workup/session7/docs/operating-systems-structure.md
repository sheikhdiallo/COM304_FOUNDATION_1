[Main Menu](../../sessions/README.md) | [session7](../../session7/) | [Operating System Structure](../docs/operating-systems-structure.md)

# The origins of the Linux Operating System

In the 1970's AT&T developed the original C programming language and used this to write a new operating system called `Unix`.
Gradually Unix and C became increasingly popular and computer manufacturers began developing their own variants to run on their own workstations; 

* HPUX - Hewlett Packard
* Solaris - Sun Microsystems
* AIX - IBM
* Ultrix - Digital Equipment Corporation

The CPU's underlying these systems were also significantly different with IBM hardware using PA-RISC processors and Sun using SPARC (Scalable Processor ARChitecture).

In theory, a program written in C to run on a Unix OS could run on any of these variants but there were sufficient differences that this was not the case.

This lead to the development of the [POSIX Compliant Unix standard](https://en.wikipedia.org/wiki/POSIX) which standardised the system calls across unix systems.

In parallel with this, [Richard Stallman](https://en.wikipedia.org/wiki/Richard_Stallman) who was a researcher at MIT, became increasingly annoyed with the way companies were hiding the details of their operating systems by keeping their programs 'closed source'. 
Stallman resigned from MIT in 1983 and started developing a Unix like operating system which would be free for anyone to use and would be published as open source program. 
He developed the `gcc` compiler and a variety of software utilities released as part of the [GNU project](https://www.gnu.org/home.en.html)

A key innovation was to publish the software under the [Copy Left GPL licence](https://en.wikipedia.org/wiki/GNU_General_Public_License) which forced people who copied or extended the source code to publish their work under the same licence.

At the 1990's, [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) began a Masters project at the University of Helsinki trying to develop a Unix kernel which would work on low cost Intel Processors.
He discovered the GNU project in 1991 and realised that the kernel he was developing could be combined with the GNU utilities to create a fully open source operating system.

The first Linux prototypes were publicly released in late 1991 and Version 1.0 was released on 14 March 1994.

Linux gradually became increasingly popular with researchers and hobbyists and as it increasingly appeared to become a viable alternative to paid for operating systems, companies and not-for-profit groups emerged which began to support `distributions` of Linux.
Linux has since grown to be the major operating system powering the cloud and the internet.

Today there are [many Linux distributions](https://en.wikipedia.org/wiki/List_of_Linux_distributions) which can primarily be categorised based upon the packaging mechanism they use.

The [Debian project](https://www.debian.org/doc/manuals/project-history/intro.en.html), which uses `.pkg` packages is the basis of [Ubuntu](https://ubuntu.com/) and [Raspberry OS](https://www.raspberrypi.com/software/)

Canonical, which distributes Ubuntu, has an estimated market cap between $40–59 million

The [Fedora project](https://fedoraproject.org/) which uses `.rpm` packages is the basis of [Red Hat Enterprise Linux](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) and its various variants, [Centos](https://www.centos.org/), [Rocky linux](https://rockylinux.org/) etc.

Red Hat was acquired by [IBM in 2019 for $34 billion](https://www.redhat.com/en/about/press-releases/ibm-closes-landmark-acquisition-red-hat-34-billion-defines-open-hybrid-cloud-future)

In addition Android is also based upon a modified Linux core.

# Operating System Structure

Most Operating systems consist of a `Kernel`, a set of shared services which run in `kernel space` and a set of `utilities` which operate in `user space`.

The figure below highlights some of the key components in the Linux operating system.

![alt text](../docs/images/linuxLayers.png "Figure linuxLayers.png")

[Source wikipedia](https://en.wikipedia.org/wiki/User_space_and_kernel_space)

A key aspect of Linux is that there are many choices which can be made as to which libraries are used to provide services in any particular layer.
In principle, this makes a Linux based system much more flexible and adaptable than a windows system.

## kernel

The Kernel is the minimal viable set of processes which provide the core operating system services.
This includes the scheduler, device drivers, virtual memory management and file systems.

## File Systems and Security

The Linux file system is organised hierarchically with (more or less) standard locations for different types of files.
![alt text](../docs/images/linuxLayers.png "Figure linuxLayers.png")

permissions

## User Interface

Early UNIX systems had simple ASCII terminal based user interfaces offering a Command Line interface (CLI) which can be accessed using SSH.

The [X window system](https://en.wikipedia.org/wiki/X_Window_System) was released by MIT in 1987 and has been the go-to windows graphical interface for UNIX and Linux for many years.

More recently, the [Wayland](https://wayland.freedesktop.org/) replacement for the X11 window system protocol has been making progress.

Both X and Wayland are options for later Raspberry Pi'ss

## Language Systems




## Boot System Structure

BIOS / DOS / GRUB / Bootstrap

## Key Shell Commands

## Package Management

Exercise  [Installing Apache Web Server](../docs/package-management-apache.md)






