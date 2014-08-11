# General Features

When evaluating different stacks to solve your Web Backend needs, it's very useful to have a global overview of the general feaures available. The following information aims to cover the most important topics and highlights of [Duda I/O](http://duda.io):

* Event Driven / Non-blocking
* Workers
* Lightweight
* Service Oriented
* Objects
* Packages

Below a brief description of each mentioned feature.

## Event-driven / Non-blocking

The whole stack is based in a non-blocking model at networking level, that means all I/O operations over Network interfaces are deferred to the [Kernel](http://kernel.org) and retaken once a notification is delivered into the user-space service.

>Is good to mention that a non-blocking model will not reduce the computing time or delays caused by the blocking calls used in your web service, for that specific topic and possible workarounds please refer to the _Duda-Threads_ implementation (co-routines).

## Workers

When the [Duda I/O](http://duda.io) stack starts, it spawn a fixed number of Workers, in technical tems _Operating System Threads_ (Posix Threads), providing new paths to scale on High Loads when working in multiple CPU (or Cores) architecture.

Each worker runs an even loop through a _Polling_ mechanism to work over Non-blocking sockets, so in short terms each _Worker_ is capable to handle thousands of connections or more depending of the system setup. The balancing of connections is done by the Monkey Scheduler or the [Linux Kernel](http://kernel.org) depending of what was specified in the configuration.

> A single Worker is enough to handle thousands of connections.

## Lightweight

In our context, _Lightweight_ means that the core and the general components around it are pretty optimized and able to work on any kind of condition without waste system or HW resources.

For a normal web service running, the global size of the running components in memory can be around of 500KB. The memory used will depends of your web service implementation and packages loaded.

> Enterprise Linux and Embedded Linux are Duda I/O targets.

## Service oriented

One of the principal [Duda I/O](http://duda.io) features, is that it allow to register multiple web services under the same HTTP instance, as well each service can be assigned to a different Virtual Host (a Virtual Host can hold multiple web services).

Services can be accessed through defined URL maps or REST interfaces. Different routing models are provided to accomplish this goal.

## Objects

When building a _Web Service_, a set of C pseudo-objects are exported to perform the setup and define callbacks for certains events in the service. Most of the objects behaves as helpers to build responses and minimize the developer effort. Some API Objects available allows to handle Requests, Responss, Sessions, Cookies, Events, etc.

For more details about the core Objects available please refer to the API section on this document.

## Packages

As said previously, [Duda I/O](http://duda.io) is _Lightweight_ and one of the internal policies is: load just what you need. For those common third party features such as JSON, Encoding, Database Access, NoSQL and others, exists a Package interface where they can be loaded on demand.

A _Web Service_ can define which distributed package will be used on runtime. Those packages are represented as Objects too and they provide their own API. The current list of Packages available can be seen in detail in the _Packages Section_.
