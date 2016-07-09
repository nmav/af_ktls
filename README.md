[![Build Status](https://travis-ci.org/nmav/af_ktls.svg?branch=master)](https://travis-ci.org/ktls/af_ktls)

# Linux Kernel TLS/DTLS Socket

*Note that the implementation is under heavy development. Use on your own risk!*

This kernel module introduces an ```AF_KTLS``` socket. ```AF_KTLS``` socket can
be used to transmit data over TLS 1.2 using TCP or DTLS 1.2 using UDP.
Currently, there is supported only AES GCM cipher.

The socket does data transmission, the handshake, re-handshaking and other
control messages have to be served by user space using appropriate libs such as
OpenSSL or Gnu TLS.  ```AF_KTLS``` socket appears to be faster especially for
transmitting files without user space (buffered-copy) interaction (using
```sendfile(2)``` or ```splice(2)```).

The socket uses [RFC5288
implementation](http://thread.gmane.org/gmane.linux.kernel/2091838) proposed on
Linux crypto mailing list by Dave Watson from Facebook. Changes made by this
patch were not merged, so you need to apply this patch in order to test
```AF_KTLS``` socket implementation. If you want to look at benchmarking
scenarios or test your use case speed impact, visit [AF_KTLS
tool](https://github.com/fridex/af_ktls-tool).

You can find precompiled kernel for Fedora 23 with RFC 5288 patch applied
[here](http://209.132.179.123:5000/).

See [issues](http://github.com/fridex/af_ktls/issues) for awaiting
enhancements or bugs.

See also [AF_KTLS tool](https://github.com/fridex/af_ktls-tool), [AF_KTLS
visualize](https://github.com/fridex/af_ktls-visualize).

