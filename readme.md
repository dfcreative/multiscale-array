# multiscale-array [![unstable](http://badges.github.io/stability-badges/dist/unstable.svg)](http://github.com/badges/stability-badges)

Create multiple scales representation for an array (see [scale-space](https://en.wikipedia.org/wiki/Scale_space) for the concept). It is simplest form of convolution with resampling, where the upper level is perfectly 2 times less than the lower level, with each value made up of two values from the previous level. Similar to mipmaps, but 1d.

[![npm install multiscale-array](https://nodei.co/npm/multiscale-array.png?mini=true)](https://npmjs.org/package/multiscale-array/)

```js
const multiscale = require('multiscale-array')

let data = Array(1e7)
let scales = multiscale(data, {
	maxScale: 65536,
	reduce: (a, b) => a*.5 + b*.5
})

//recalculate scales for the data range, this is O(2N)
scales.update(from?, to?)

//pass new data and recalc scales for it
scales.update(newData, from?, to?)

//get data for the scale 2⁴
scales[4];

//subset scales, like slice but mutable (!)
scales.subset(from, to)
```

