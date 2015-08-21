# Coverage objects

## Coverage properties

### .type

The type of the coverage given as a URI, e.g. http://coveragejson.org/def#ProfileCoverage. It corresponds to the domain type and is suitable for choosing an appropriate implementation for rendering without loading domain data.

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
