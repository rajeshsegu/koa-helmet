koa-helmet
==========

[![Version](https://img.shields.io/npm/v/koa-helmet.svg?style=flat-square)](https://www.npmjs.com/package/koa-helmet)
[![Dependency Status](https://img.shields.io/david/venables/koa-helmet.svg?style=flat-square)](https://david-dm.org/venables/koa-helmet)
[![Build Status](https://img.shields.io/travis/venables/koa-helmet/koa-1.svg?style=flat-square)](https://travis-ci.org/venables/koa-helmet)
[![Downloads](https://img.shields.io/npm/dm/koa-helmet.svg?style=flat-square)](https://www.npmjs.com/package/koa-helmet)

koa-helmet is a wrapper for [helmet](https://github.com/helmetjs/helmet) to work with [koa](https://github.com/koajs/koa).

NOTE
----

This branch supports Koa 0.x and 1.x.  For Koa 2 support (using Promises instead of Generators), please use the [master](https://github.com/venables/koa-helmet) branch.


Versioning
----------

* koa-helmet 1.x (koa-1 branch) supports koa 0.x and koa 1.x
* koa-helmet 2.x (master branch) supports koa 2.x


Installation
------------

```
npm install koa-helmet --save
```

Usage
-----

Usage is the same as [helmet](https://github.com/helmetjs/helmet).

Helmet offers 11 security middleware functions:

| Module | Default? |
|---|---|
| [contentSecurityPolicy](https://helmetjs.github.io/docs/csp/) for setting Content Security Policy |  |
| [dnsPrefetchControl](https://helmetjs.github.io/docs/dns-prefetch-control) controls browser DNS prefetching | ✓ |
| [frameguard](https://helmetjs.github.io/docs/frameguard/) to prevent clickjacking | ✓ |
| [hidePoweredBy](https://helmetjs.github.io/docs/hide-powered-by) to remove the X-Powered-By header | ✓ |
| [hpkp](https://helmetjs.github.io/docs/hpkp/) for HTTP Public Key Pinning |  |
| [hsts](https://helmetjs.github.io/docs/hsts/) for HTTP Strict Transport Security | ✓ |
| [ieNoOpen](https://helmetjs.github.io/docs/ienoopen) sets X-Download-Options for IE8+ | ✓ |
| [noCache](https://helmetjs.github.io/docs/nocache/) to disable client-side caching |  |
| [noSniff](https://helmetjs.github.io/docs/dont-sniff-mimetype) to keep clients from sniffing the MIME type | ✓ |
| [referrerPolicy](https://helmetjs.github.io/docs/referrer-policy) to hide the Referer header |  |
| [xssFilter](https://helmetjs.github.io/docs/xss-filter) adds some small XSS protections | ✓ |

You can see more in [the documentation](https://helmetjs.github.io/docs/).

Note:
-----

In order to work well with the helmet HSTS module, koa-helmet will augment
`this.req` to include a `secure` boolean to determine if the request
is over HTTPS.

Example
-------

```js
var koa = require('koa');
var helmet = require('koa-helmet');
var app = koa();

app.use(helmet());
app.use(function *(){
  this.body = 'Hello World';
});

app.listen(4000);
```
