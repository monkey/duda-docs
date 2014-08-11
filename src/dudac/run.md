# Running a Web Service

This is the easiest step once the Development Environment is already installed, the following are the options provided by __DudaC__:

Option | Value         | Description
-------|---------------|-------------
-w     | PATH          | Specify the web service sources path
-M     | 'k1=v1,kn=vn' | Override some web server config key/value
-u     |               | Redirect server output to STDOUT

In order to run a Web Service, the __-w__ option allows to specify the path where the sources of the service are available. On each run __DudaC__ will issue a _make_ to re-compile the service in question.

As the service runs over a configurable HTTP server, it allows to modify specific configuration keys through the __-M__ option, it support multiple key values in the format _key1=value1,key2=value2_. This is an example of running a service with custom configuration:

```Bash
$ dudac -M 'Port=10000,Listen=192.68.5.3,Workers=5' -w /path/to/service
```

The configuration says it will use the TCP Port 10000, listening only on the interface owned by 192.68.5.3 IP address and the HTTP core will spawn five workers. For a complete list of the keys available please refer to the [Monkey Server Core](http://monkey-project.com/documentation/1.5/configuration/server.html) documentation section.

If for some reason you are printing information to the standard output, you can get those messages enabling the __-u__ option.

## Example

This is an example running the [001_hello_world](https://github.com/monkey/duda-examples/tree/master/001_hello_world) service:

```Bash
dudac -w ../duda-examples/001_hello_world
Duda Client Manager - v0.23
http://duda.io
http://monkey-project.com

[+] WebService  : clean                           [OK]
[+] WebService  : build                           [OK]
[+] Monkey      : configure HTTP Server           [OK]
[+] Service Up  : http://localhost:2001/hello/
```

The output says the service is _reachable_ through the address  http://localhost:2001/hello/ , doing a simple test with _Curl_ we get:

```Bash
$ curl -i http://localhost:2001/hello/
HTTP/1.1 200 OK
Server: Monkey/1.4.0
Date: Mon, 11 Aug 2014 18:11:11 GMT
Content-Length: 12

Hello World!
```

This is good enough, so next chapters will provide more information about available example services, internals and different aspects of this great technology.
