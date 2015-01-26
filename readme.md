## [![npm versi][npmjs-img]][npmjs-url] [![mit license][license-img]][license-url] [![build status][travis-img]][travis-url] [![coverage status][coveralls-img]][coveralls-url] [![deps status][daviddm-img]][daviddm-url]

> Flexible and cross-platform executing commands. **[Hybrid][hybridify], Async and Promise API.**


## Install
```bash
$ npm install exec-cmd
$ npm test
```


## Usage
> For more use-cases see the [tests](./test.js)

```js
var exec = require('exec-cmd');
var promise = exec('echo', [
  'hello world'
])
.then(function(stdout) {
  //=> 'hello world'
})
.catch(function(stderr) {
  //=> ''
})

var promise = exec('echo', [
  'hello world'
], function(err, res) {
  assert(!err)
  // console.log('from cb')
  strictEqual(res.trim(), 'hello world');
})
.then(function(stdout) {
  // console.log('from then (promise)')
  strictEqual(stdout.trim(), 'hello world');
  done();
})
.catch(function(stderr) {
  /* istanbul ignore next */
  notStrictEqual(stderr.trim(), 'hello world');
  /* istanbul ignore next */
  done();
})
```


## API
### [execCmd](./index.js#L43)
> Hybrid execute command via spawn

* `<cmd>` **{String}**  
* `<args>` **{Array|Function}**  
* `[opts]` **{Object|Function}**  
* `[callback]` **{Function}**  
* `returns` **{Promise}**  

**Example:**

```js
var exec = require('exec-cmd');
var promise = exec('echo', [
  'hello world'
], function __cb(err, res) {
  // as usual
})
.then(function(res) {
  //=> res[0] is code
  //=> res[1] is stdout
  //=> res[1] === 'hello world'
})
.catch(function(err) {
  //=> null || undefined?
})
```


## Author
**Charlike Mike Reagent**
+ [gratipay/tunnckoCore][author-gratipay]
+ [twitter/tunnckoCore][author-twitter]
+ [github/tunnckoCore][author-github]
+ [npmjs/tunnckoCore][author-npmjs]
+ [more ...][contrib-more]


## License [![MIT license][license-img]][license-url]
Copyright (c) 2015 [Charlike Mike Reagent][contrib-more], [contributors][contrib-graf].  
Released under the [`MIT`][license-url] license.


[npmjs-url]: http://npm.im/exec-cmd
[npmjs-img]: https://img.shields.io/npm/v/exec-cmd.svg?style=flat&label=exec-cmd

[coveralls-url]: https://coveralls.io/r/hybridables/exec-cmd?branch=master
[coveralls-img]: https://img.shields.io/coveralls/hybridables/exec-cmd.svg?style=flat

[license-url]: https://github.com/hybridables/exec-cmd/blob/master/license.md
[license-img]: https://img.shields.io/badge/license-MIT-blue.svg?style=flat

[travis-url]: https://travis-ci.org/hybridables/exec-cmd
[travis-img]: https://img.shields.io/travis/hybridables/exec-cmd.svg?style=flat

[daviddm-url]: https://david-dm.org/hybridables/exec-cmd
[daviddm-img]: https://img.shields.io/david/hybridables/exec-cmd.svg?style=flat

[author-gratipay]: https://gratipay.com/tunnckoCore
[author-twitter]: https://twitter.com/tunnckoCore
[author-github]: https://github.com/tunnckoCore
[author-npmjs]: https://npmjs.org/~tunnckocore

[contrib-more]: http://j.mp/1stW47C
[contrib-graf]: https://github.com/hybridables/exec-cmd/graphs/contributors

***

_Powered and automated by [kdf](https://github.com/tunnckoCore), January 26, 2015_


[hybridify]: https://github.com/hybridables/hybridify
