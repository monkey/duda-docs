# Duda I/O Documentation

[Duda I/O](http://duda.io) is a _High Performance Web Services Framework_ to develop scalable services for Linux and Embedded Linux.

The following content is the source of [Duda I/O](http://duda.io) documentation project.

## Requirements

This documentation is generated using [Gitbook](http://gitbook.io), so the following tools needs to be installed:

### NPM

```
$ sudo apt-get install npm
```

### Gitbook

```shell
$ sudo npm install gitbook
$ sudo npm install gitbook-plugin-richquotes
```

## How the documentation is built

All documentation is made in GIT Flavored Markdown format and is rendered using the [Gitbook](https://github.com/GitbookIO/gitbook) tool. To generate a HTML documenation from this source please issue the following command:

```shell
$ gitbook serve -p 9000 src/
```

Then point your browser at http://127.0.0.1:9000/ to see the HTML documents. For more options check the Gitbook help.
