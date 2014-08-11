# Setup

The tool provide several options that can be grouped in three categories:

* Prepare the Development Environment
  * Stack Build Options
  * Profiling and Trace
  * HTTP Server Options
* Others

## Prepare the Development Environment

### Stack Build Options

Option | Description
-------|-------------
-V     | Set the API level (default: 1)
-s     | Get stack sources from GIT using HTTPS protocol
-g     | Get stack sources from GIT using Git protocol
-F     | Force mode, rebuild the _Stage_ area
-r     | Reset the stack environment.

Before to set the Development Environment, is required to know which _API Level_ or _DST_ branch is going to be used, by default __DudaC__ will offer the most stable level. For more details about the levels available please refer to the [Versions](../about/versions.md) section.

The next step is to download the [Stack Components](getting_started/stack_components.md). When preparing a Development Environment, the tool requires to download a fresh copy of each component, this can be done using the __-s__ or __-g__ options. Both of them will retrieve sources from our [Github](https://github.com/monkey) repositories using either HTTPS or GIT protocols. 

The following is an example to get the stack downloaded and build:

```Bash
$ dudac -s
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

The output describe what was done on each phase, if you look carefully you will realize that everything was obtained from GIT repositories, the level was changed to __DST-1__ and then it was compiled.

If for some reason you want to remove the Stack just downloaded and built, you can use the __-r__ option which will reset the Development Environment. It will delete the whole content of the path _~/.dudac/_.

### Profiling and Trace Options

[Duda I/O](http://duda.io) stack provides some extra options for debugging and profiling to be used on build time, those options can be used directly from __DudaC__, here is a summary of the modes available:

Option | Description
-------|-------------
-A     | Use libc memory allocator instead of Jemalloc (disabled)
-X     | Enable Jemalloc statistics (disabled)
-J     | Enable Jemalloc profiling and leaks detection (disabled)
-T     | Enable Linux Trace Toolkit (disabled)

By default, for performance and scalability reasons, the stack uses the [Jemalloc](http://www.canonware.com/jemalloc) memory allocator, which is distributed as part of the sources of the stack. The __-A__ option instruct __DudaC__ to do __not__ use [Jemalloc](http://www.canonware.com/jemalloc) and just link to the standard system memory allocator: libc.

[Jemalloc](http://www.canonware.com/jemalloc) provide several options that are useful for developing and troubleshooting process. When enabling the __-X__ option, the library will compile with the statistics mode enabled. More details about this feature on the [Jemalloc Wiki Page](https://github.com/jemalloc/jemalloc/wiki/Use-Case%3A-Basic-Allocator-Statistics). Another option available is to enable _profileing_ and _leak detection_, this can be enabled with the __-J__ option and it usage is described [here](https://github.com/jemalloc/jemalloc/wiki/Use-Case%3A-Leak-Checking).

As described in the [Stack Components](../getting_started/components.md) section, [Monkey HTTP Server](http://monkey-project.com) is a fundamental part of the stack and it natively supports [Linux Trace Toolkit (LTTng)](https://lttng.org). When enabling this feature is possible to trace several core statuses that are very useful when troubleshooting stack internals. For more details about it please refer to the [Monkey Debugging](http://monkey-project.com/documentation/1.5/debugging/README.html) documentation site.


### HTTP Server Options

On build time, there are a few options for the HTTP Server:

Option | Description
-------|-------------
-p     | Set TCP port (default 2001)
-S     | Web Service will run with SSL mode enabled

By default, the stack uses the TCP port 2001, this can be changed with the __-p__ option on build time. Also if desired to use SSL for secure communication over your services, specifying the __-S__ option will take care to build the SSL support and configure the service with some self-generated certificates. Those certificates can be changed later in the configuration.

### Other Options

These options are not part of the setup process but are common enough to understand what are they for:

Option | Description
-------|-------------
-h     | Print help of DudaC
-v     | Print DudaC version
