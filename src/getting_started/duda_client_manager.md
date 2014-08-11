# Duda Client Manager / DudaC

When dealing with different software components to build a specific solution, it's important to have tools to setup a proper development environment which takes care of validate the system requirements and dependencies. Reducing entry complexity it's a must when working with frameworks for the first time, so the focus can stay on development and not in setup tasks.

Duda Client Manager (aka DudaC), is a tool made in Python with the objective to create a working development environment for who wants to build scalable web services using [Duda I/O](http://duda.io). It takes care to download the stack dependencies from GIT repositories and create a stage directory with a compiled stack for further use when running the service.

## Getting started with DudaC

__DudaC__ can be obtained directly from our main site, [PyPi](http://https://pypi.python.org/pypi) or through the main GIT repository.

### Main Site

To get the latest stable version of __DudaC__ please visit the following link:

http://duda.io/downloads

### PyPi

The software URL on PyPi index is https://pypi.python.org/pypi/dudac, you can fecth a copy of the latest version from the web page or installing it directly from the command line, e.g:

```Bash
$ pip install dudac
```

Check if it was installed just typing _dudac_:

```Bash
$ dudac
```

### Git

All source code around [Duda I/O](http://duda.io) is published on GIT repositories on [Github](http://github.com). To fetch the development version you can clone the main repository:

```Bash
$ git clone https://github.com/monkey/dudac
```

## Preparing the Environment

Once the tool is in place the first step is to tell it to download the required software components, this is just one time step, depending of your network bandwith it should not take more than two or three minutes:

```Bash
$ cd dudac/
$ ./dudac -s
```

The -g option tells dudac to use GIT protocol to fetch the components, if for some reason it cannot be used due to some network restriction for the host where it runs, the flag -s can be used instead to fetch using SSH. An expected output in the screen is as follows:

```
Duda Client Manager - v0.23
http://duda.io
http://monkey-project.com

[+] Monkey: cloning source code                  [OK]
[+] Duda: cloning source code                    [OK]
[+] GIT Monkey  : switch HEAD to 'dst-1'         [OK]
[+] GIT Duda    : switch HEAD to 'dst-1'         [OK]
[+] GIT Monkey  : archive                        [OK]
[+] GIT Duda    : archive                        [OK]
[+] Monkey      : prepare build                  [OK]
[+] Monkey      : building                       [OK]
```

Some compilation warnings are expected, but they are not something to worry about it. Having an output as described below means everything is ready to start running or build web services using Duda I/O.

### Staging directory

If you want to know more about what DudaC did, you can check your home directory under ~/.dudac . There you will find the content recently downloaded, it will have the following structure:

```
$ ls -l ~/.dudac/
total 12
drwxrwxr-x    9 .. .. 4096 Sep 17 10:17 duda
drwxrwxr-x   13 .. .. 4096 Sep 17 10:16 monkey
drwxrwxr-x    3 .. .. 4096 Sep 17 10:19 stage
```

Each directory represents:

Name  | Description
------|--------------
duda  | A GIT clone repository of the framework it self, the plugin that hooks into the HTTP server stack, expose the API and allow to run services.
monkey|A GIT clone repository of Monkey HTTP Server
stage | directory that contains GIT archive copies for duda/ and monkey/ directories. The main purpose of this directory is to work as the build environment home where Monkey and Duda are built together. Every time a web service is created with DudaC, will use the stage/ directory as the base stack.

## DudaC options

When running DudaC several options are available depending of the task required to accomplish, we can separate them into a few categories:

### Development Environment

Option | Description
-------|-------------
-g |obtain stack software components using GIT protocol. This is usually the common option to start retrieving the software components from it mains GIT repositories. If for some reason GIT protocol cannot be used directly, switch to SSH mode described above.
-s | obtain stack software components using SSH protocol. Instead of use a direct GIT protocol communication, perform all communication over a SSL channel using the remote SSH service. In most of cases it works as a workaround to -g mode.
-r | reset the development environment. This option will remove the downloaded software components that resides on ~/.dudac directory. If for some reason this command is run, to restore the environment is required a further -g or -s to prepare everything again  from scratch.

### Running a Web Service

-f: use the fast-run mode.

By default when running a web service, the stack will be compiled from scratch. In order to skip that the fast-run mode can be used.

-p: set listener TCP port.

By default a web service will start listening on TCP port 2001. In order to use a different TCP port this option can be used. Note that if you want to use a TCP port < 1024, it will require root privileges.

-S: Enable the Secure Socket Layer (SSL).

By default the stack use plain sockets for it communication, enabling this option the environment will configure the SSL layer and generate it owns certificates.

-M: Override HTTP server configuration.

When the HTTP server is started, it reads it monkey.conf configuration file (located on ~/.dudac/stage/monkey/conf/monkey.conf). It contains a set of key/value pair settings that alter the server behavior, some of them are: Port, Listen, Workers, Timeout, Pidfile, Indexfile, HideVersion, Resume, KeepAlive, KeepAliveTimeout, MaxKeepAliveRequest, MaxRequestSize, SymLink, TransportLayer and DefaultMimeType.

If we want the service to bind a specific interface on address 192.168.5.3 and let the server use 5 workers the flag should be use as:

    -M 'Listen=192.168.5.3,Workers=5'

-u: redirect output to the screen.

When the service starts, by default all output messages are dropped. Enabling this option all output will be redirected to the standard output (STDOUT).
Other options

-h: print help.

Basic command to display all options available on the screen.

-v: print DudaC version.
