# Coverage objects

## Coverage properties

### .type

The coverage type is a URI that describes which concept the coverage represents, e.g. http://www.topografix.com/GPX#Track. It may be used by implementations to choose a more appropriate visualization than by just simply looking at the domain type (e.g. http://coveragejson.org/def#Trajectory)

### .domainType

The domain type of the coverage given as a URI, e.g. http://coveragejson.org/def#Profile. The domain type is typically enough to choose a (possibly generic) implementation for visualization/processing. This property is identical to the [`Domain.type`](Domain.md) property. It allows to make early decisions without actually loading the domain with `.loadDomain()`.

### .bbox

A geographical (WGS84) 2D bounding box of the coverage as an array `[southWestLon, southWestLat, northEastLon, northEastLat]` with values in degrees.

### .timeExtent

The time period which this Coverage covers as an array `[start, end]` of [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) objects.

### .verticalExtent

... as always, tricky

### .parameters

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) from key to [`Parameter`](Parameter.md) object. The key is a short alias of a Parameter, typically what is called a "variable name" or similar.

## Coverage methods

### .loadDomain()

The `loadDomain()` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which loads the domain data and provides a [`Domain`](Domain.md) object in its callback.

#### Examples

```js
cov.loadDomain().then(function(domain) {
  console.log(domain.type) // "http://coveragejson.org/def#Grid"
})
```

### .loadRange(paramKey)

The `loadRange` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which loads the requested range data and provides a [`Range`](Range.md) object in its callback.

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

## subsetByIndex(constraints)

If defined, returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which provides a copy of this [`Coverage`](Coverage.md) object with the domain subsetted by indices. If this function is not defined, then this operation is not supported. The coverage and/or domain type may be different than in the original coverage.

### Parameters

`constraints` - An object which describes the subsetting constraints. Every property of it refers to an axis name as defined in `Domain.names`, and its value must either be an integer, an array of integers, or an object with `start`, `stop`, and optionally `step` (defaults to 1) properties whose values are integers. All integers must be non-negative, `step` must not be zero. A simple integer constrains the axis to the given index, an array to a list of indices, and a start/stop/step object to a range of indices: If `step=1`, this includes all indices starting at `start` and ending at `stop` (exclusive); if `step>1`, all indices `start, start + step, ..., start + (q + r - 1) step` where `q` and `r` are the quotient and remainder obtained by dividing `stop - start` by `step`.

### Example

```js
cov.subsetByIndex({t: 4, z: {start: 10, stop: 20}, x: [0,1,2] }).then(function(subsetCov) {
    console.log(subsetCov.bbox)
}
```
