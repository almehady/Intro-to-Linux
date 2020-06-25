# Linux Philosophy and Concepts

## Linux History

The Linux distributions created in the mid-90s provided the basis for fully free (in the sense of freedom, not zero cost) computing and became a driving force in the open source software movement. In 1998, major companies like IBM and Oracle announced their support for the Linux platform and began major development efforts as well.

Today, Linux powers more than half of the servers on the Internet, the majority of smartphones (via the Android system, which is built on top of Linux), and all of the world’s most powerful supercomputers.

## Lunux Terminology
**Kernel** : Glue between hardware and applications. For example - Lunux Kernel

**Distribution or Distro** - Collection of software making up a Linux based OS. For example - Feroda, CentOS, Ubuntu

**Boot Loader** : Program that boots the operating system. For example - GRUB or ISOLINUX

**Service** : Program that runs as a background process. Example- httpd, nfsd, ftpd and named

**File System** : Method for sorting and organizing files. Example - ext3, ext4, FAT, XFS, NTFS and Btrfs

**X Window System** : Graphical subsystem on nearly all Linux systems

**Desktop Environment** : Graphical user interface on top of the operating system. Example - GNOME, KDE, Xfce and Fluxbox

**Command line** : Interface for typing commands on top of the operating system.

**Shell**: Command line interpreter that interprets the command line input and instructs the operating system to perform any necessary task and commands. Example - bash, tcsh and zsh



## Linux Distributions
The Linux kernel is the core of the operating system. A full Linux distribution consists of the kernel plus a number of other software tools for file-related operations, user management, and software package management. Each of these tools provides a part of the complete system. Each tool is often its own separate project, with its own developers working to perfect that piece of the system.

While the most recent Linux kernel (and earlier versions) can always be found in The Linux Kernel Archives, Linux distributions may be based on different kernel versions. For example, the very popular RHEL 7 distribution is based on the 3.10 kernel, which is not new, but is extremely stable. Other distributions may move more quickly in adopting the latest kernel releases. It is important to note that the kernel is not an all or nothing proposition, for example, RHEL 7/CentOS 7 have incorporated many of the more recent kernel improvements into their older versions, as have Ubuntu, openSUSE, SLES, etc.

Examples of other essential tools and ingredients provided by distributions include the C/C++ compiler, the gdb debugger, the core system libraries applications need to link with in order to run, the low-level interface for drawing graphics on the screen, as well as the higher-level desktop environment, and the system for installing and updating the various components, including the kernel itself.  And all distributions come with a rather complete suite of applications already installed.