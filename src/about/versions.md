# Versions

Understanding how do we handle [Duda I/O](http://duda.io) versions is very important to know the stability level of the stack and the available API to be used.

Being [Duda I/O](http://duda.io) a development stack to write web services, stability and security is very important topic when considering any kind of deployment for a production environment. For hence we maintain stable branches for that purpose called __Duda Stable Branches__ or __DST__ for short.

Every __DST__ have it own __Long Term Support__ period, where it receive only bug fixes making sure your production service will be always able to run on a stable level. Once a __DST__ is released, no API changes or new features are added, as said, just fixes.

The following table describe the available _Branches_ and the period that they will receive official support:

Branch | HTTP Stack   |Release date         | Long Term Support
-------|--------------|---------------------|-------------------
DST-2  | Monkey v1.6  | `under development` |
[DST-1](https://github.com/monkey/duda/tree/dst-1) | Monkey v1.4  | Feb 22, 2014 | Oct 01, 2015

## HTTP Stack

[Duda I/O](http://duda.io) is build on top of [Monkey HTTP Server](http://monkey-project.com), for hence it inherits it features and stability. Each __DST__ is based on a stock version of [Monkey](http://monkey-project.com), e.g: __DST-1__ is based on stock __Monkey v1.4__.

During the __Long Term Support__ period cycle, the stack receives all relevant bug fixes that [Monkey](http://monkey-project.com) get on it upstream version. We make sure that any problem and further fix _must_ be back ported to the supported __DST__ branches.

Running a first-class HTTP stack is the key of success in terms of performance, security and general integration with different layers of software. To learn more about  [Monkey](http://monkey-project.com) please visit the official site [monkey-project.com](http://monkey-project.com).
