# Coverage objects

## Coverage properties

### .type

**TODO** as in Domain this should probably also be a URI, but maybe more generic in terms of a concept, whereas the URI in Domain defines exactly how the coordinates are structured and which properties exist, so this may be in the sense of a common authority like http://coverages.org/def/types/Profile and it could give a first hint to libraries on what to expect without looking at/loading the domain data

The type of the coverage, more specifically of its domain, as a string. One of `Grid`, `Profile`, ...

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
  console.log(domain.type) // "Grid", "Profile", ...
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
