# Stack Components

Before to proceed with the main installation of [Duda I/O](http://duda.io), we need to introduce what are the main components that conforms the stack. All of them comes integrated and work in a cooperative way:

* Duda Client Manager (DudaC)
* Monkey HTTP Server
* Duda Plugin

## Duda Client Manager or DudaC

Our main interest is to reduce complexity and provide a straightforward mechanism to start using Duda I/O right away. __Duda Client Manager__ or __DudaC__ it's the main tool that put all pieces together from scratch. It main responsibilities are:

* Build a Duda I/O runtime stack from scratch for development or production purposes.
* Provide different build options for general profiling or services trace.
* Make custom setup over the running HTTP stack.
* Manage services: start & stop.

> Note: DudaC is written in Python2

## Monkey HTTP Server

[Monkey](http://monkey-project.com) is the principal HTTP runtime of [Duda I/O](http://duda.io), it exposes a flexible event-driven core that provides also an API to extend it behavior through _Plugins_.

For more details about [Monkey](http://monkey-project.com) please refer to it official documentation here:

http://monkey-project.com/documentation

## Duda Plugin

[Duda](http://duda.io) it self is a [Monkey](http://monkey-project.com) plugin. It extend the HTTP behavior exposing a friendly C API which provides several features and a layer to hook _Web Services_. A summary of [Duda Plugin](http://duda.io) capabilities:

* Extend HTTP core configuration at Virtual Host level.
* Wrap Monkey API and expose it in a pseudo-object mode.
* Architecture to implement packages or third party features loaded on runtime by services.
* Architecture to hook Web Services.

The plugin is very powerful on terms of features. It design keeps the [Monkey](http://monkey-project.com) principles: _Fast_, _Lighweight_ & _Secure_.
