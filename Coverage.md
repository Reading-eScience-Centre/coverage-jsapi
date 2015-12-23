# Coverage objects

## Coverage properties

### .id

An optionally defined URI that serves as common identifier for this coverage.

### .type

The coverage type is a URI that describes which concept the coverage represents, e.g. http://www.topografix.com/GPX#Track. It may be used by implementations to choose a more appropriate visualization than by just simply looking at the domain type (e.g. http://coveragejson.org/def#Trajectory)

### .domainType

The domain type of the coverage given as a URI, e.g. http://coveragejson.org/def#Profile. The domain type is typically enough to choose a (possibly generic) implementation for visualization/processing. This property is identical to the [`Domain.type`](Domain.md) property. It allows to make early decisions without actually loading the domain with `.loadDomain()`.

### .bbox

If defined, an object with members `"box"` and `"srs"` where `"box"` is an array of four coordinates `[minx,miny,maxx,maxy]` describing the horizontal bounding box of the coverage and `"srs"` is a URI of the spatial coordinate reference system used for the coordinates. The value of `"srs"` will in most cases be `http://www.opengis.net/def/crs/OGC/1.3/CRS84` such that the `"box"` array has the values `[west longitude, south latitude, east longitude, north latitude]`.

### .timeExtent

The time period which this Coverage covers as an array `[start, end]` of [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) objects.

### .parameters

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) from key to [`Parameter`](Parameter.md) object. The key is a short alias of a Parameter, typically what is called a "variable name" or similar.

## Coverage methods

### .loadDomain()

The `loadDomain()` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`Domain`](Domain.md) object. Note that this method may load remote data.

#### Examples

```js
cov.loadDomain().then(function(domain) {
  console.log(domain.type) // "http://coveragejson.org/def#Grid"
})
```

### .loadRange(paramKey)

The `loadRange` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`Range`](Range.md) object that corresponds to the given parameter key. Note that this method may load remote data.

#### Parameters

`paramKey` - The key of the [`Parameter`](Parameter.md) for which to load the range

#### Examples

```js
var paramKey = 'salinity'
cov.loadRange(paramKey).then(function(range) {
  console.log(range.validMin, range.validMax)
  console.log(range.values)
})
```

### .loadRanges([paramKeys])

The `loadRanges` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) object where a key is one of the parameter keys and a value is a [`Range`](Range.md) object.

#### Parameters

`paramKeys` - An iterable of parameter keys for which to load the range data. If not given, loads all range data.

#### Examples

```js
cov.loadRanges().then(function(ranges) {
  console.log(ranges.get('salinity').values)
})
```

#### Reference implementation (ES6 syntax)

```js
function loadRanges (keys) {
  if (keys === undefined) keys = this.parameters.keys()
  keys = Array.from(keys)
  return Promise.all(keys.map(this.loadRange)).then(ranges => {
    let map = new Map()
    for (let i=0; i < keys.length; i++) {
      map.set(keys[i], ranges[i])
    }
    return map
  })
}
```

## subsetByIndex(constraints)

If defined, returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object succeeding with a copy of this [`Coverage`](Coverage.md) object with the domain subsetted in index space. If this function is not defined, then this operation is not supported. The coverage and/or domain type may be different than in the original coverage.

### Parameters

`constraints` - An object which describes the subsetting constraints. Every property of it refers to an axis name as defined in `Domain.names`, and its value must either be an integer, or an object with `start`, `stop`, and optionally `step` (defaults to 1) properties whose values are integers. Properties that have the values `undefined` or `null` are ignored. All integers must be non-negative, `step` must not be zero. An integer constrains the axis to the given index, a start/stop/step object to a range of indices: If `step=1`, this includes all indices starting at `start` and ending at `stop` (exclusive); if `step>1`, all indices `start, start + step, ..., start + (q + r - 1) step` where `q` and `r` are the quotient and remainder obtained by dividing `stop - start` by `step`.

### Example

```js
cov.subsetByIndex({t: 4, z: {start: 10, stop: 20} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```

## subsetByValue(constraints)

If defined, returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object succeeding with a copy of this [`Coverage`](Coverage.md) object with the domain subsetted in value space. If this function is not defined, then this operation is not supported. The coverage and/or domain type may be different than in the original coverage. Subsetting in value space is only supported for non-composite axes.

### Parameters

`constraints` - An object which describes the subsetting constraints. Every property of it refers to an axis name as defined in `Domain.names`, and its value must either be a number or string, or, if the axis has an ordering relation, an object with `start` and `stop` properties whose values are numbers or strings, or an object with a `target` property whose value is a number or string. Properties that have the values `undefined` or `null` are ignored. A number or string constrains the axis to exactly the given value, a start/stop object to the values intersecting the extent, and a target object to the value closest to the given value.

### Example

```js
cov.subsetByValue({t: '2015-01-01T01:00:00', z: {start: -10, stop: -5} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```

### Example

```js
cov.subsetByValue({z: {target: -10} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```
