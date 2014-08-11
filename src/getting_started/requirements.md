# Requirements

[Duda I/O](http://duda.io) is made exclusively for __Linux__ and certified to work on specific distributions. This document assumes you are running one of the following versions:

Linux Distribution | Version      | Link
-------------------|--------------|-------
Ubuntu             | 14.04 LTS (Trusty Tahr) | http://releases.ubuntu.com/14.04/
Redhat             | `under review` |
CentOS             | `under review` |

## Hardware

The stack is made for __x86__ and __x86_64__ architectures, as well it works pretty optimized on __ARM__ processors. It can be used from an Embedded Linux board to any high-end production server.

A vanilla Duda I/O running in memory should consume around __500KB__, but based on the general setup, packages, expected load and the requirements for the running _Web Service_, it may vary and require more resources. It can be optimized and customized for any type of need.

## Ubuntu packages

When running on the certified Ubuntu version, please proceed to install the following packages that are required to setup the development environment:

 * build-essential
 * python2.7

> The Python tool is just required if you are using DudaC tool, all other components just need the GNU C (gcc) or Clang compilers.

You can issue the following command to fill the dependencies:

```Bash
$ sudo apt-get install build-essential python2.7
```

## Kernel Version

The stack requires that you are running an updated [Linux Kernel](http://kernel.org) version, is assumed you are using a stock Kernel provided by your main distribution:

Kernel Version | Status
---------------|--------
>= 3.9         | optimal
>= 3.2         | desired

The Kernel version plays an important role on which features the stack is able to use, most of them relies on specific system calls or TCP features to improve performance. Using the _optimal_ version is suggested for a high demand environment.
