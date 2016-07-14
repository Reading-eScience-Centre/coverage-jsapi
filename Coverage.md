# Coverage objects

## Coverage properties

### .type

The constant `"Coverage"`.

### .id

An optionally defined URI that serves as common identifier for this coverage.

### .domainType

If defined, then the coverage has a domain that follows the given domain type, e.g. `'http://covjson.org/def/domainTypes#Trajectory'`.

### .parameters

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) from key to [`Parameter`](Parameter.md) object. The key is a short alias of a Parameter, typically what is called a "variable name" or similar.

### .loaded

A boolean which indicates whether all coverage data is already loaded in memory. If `true` then this typically means that calls to `.loadDomain()`, `.loadRange()`, `.loadRanges()`, `.subsetByIndex()`, and `.subsetByValue()` will not invoke a network request.

## Coverage methods

### .loadDomain()

The `loadDomain()` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`Domain`](Domain.md) object. Note that this method may load remote data.

#### Examples

```js
cov.loadDomain().then(function(domain) {
  console.log(domain.domainType) // ["http://covjson.org/def#Grid"]
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
  console.log(range.get({x: 0, y: 2, t:0}))
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
  if (!keys) {
    keys = this.parameters.keys()
  }
  return Promise.all([...keys].map(this.loadRange)).then(ranges =>
    new Map(keys.map((key,i) => [key,ranges[i]]))
  )
}
```

### .subsetByIndex(constraints[, options])

If defined, returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object succeeding with a copy of this [`Coverage`](Coverage.md) object with the domain subsetted in index space. If this function is not defined, then this operation is not supported. The coverage and/or domain profiles may be different than in the original coverage.

#### Parameters

`constraints` - An object which describes the subsetting constraints. Every property of it refers to an axis name as defined in `Domain.axes`, and its value must either be an integer, or an object with `start`, `stop`, and optionally `step` (defaults to 1) properties whose values are integers. Properties that have the values `undefined` or `null` are ignored. All integers must be non-negative, `step` must not be zero. An integer constrains the axis to the given index, a `start`/`stop`/`step` object to a range of indices: If `step=1`, this includes all indices starting at `start` and ending at `stop` (exclusive); if `step>1`, all indices `start, start + step, ..., start + (q + r - 1) step` where `q` and `r` are the quotient and remainder obtained by dividing `stop - start` by `step`.

`options` - Optional. An options object.

`options.eagerload` - Optional. Only applies when the operation is run against a server. If `true`, indicates a preference to the server to return all data in a single response, instead of including links for loading further data in an on-demand (lazy) manner. The server may not support or honor the preference. Note that this preference, whether fulfilled or not, has no influence on the JavaScript API.

#### Example

```js
cov.subsetByIndex({t: 4, z: {start: 10, stop: 20} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```

#### Example

```js
cov.subsetByIndex({t: 4}, {eagerload: true).then(function(subsetCov) {
    // work with subsetted coverage
}
```

### .subsetByValue(constraints[, options])

If defined, returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object succeeding with a copy of this [`Coverage`](Coverage.md) object with the domain subsetted in value space. If this function is not defined, then this operation is not supported. The coverage and/or domain profiles may be different than in the original coverage. Subsetting in value space is only supported for non-composite axes.

#### Parameters

`constraints` - An object which describes the subsetting constraints. Every property of it refers to an axis name as defined in `Domain.axes`, and its value must either be a number or string, or, if the axis has an ordering relation, an object with `start` and `stop` properties whose values are numbers or strings, or an object with a `target` property whose value is a number or string. Properties that have the values `undefined` or `null` are ignored. A number or string constrains the axis to exactly the given value, a `start`/`stop` object to the values intersecting the extent, and a `target` object to the value closest to the given value.

`options` - Optional. An options object.

`options.eagerload` - Optional. Only applies when the operation is run against a server. If `true`, indicates a preference to the server to return all data in a single response, instead of including links for loading further data in an on-demand (lazy) manner. The server may not support or honor the preference. Note that this preference, whether fulfilled or not, has no influence on the JavaScript API.

#### Example

```js
cov.subsetByValue({t: '2015-01-01T01:00:00', z: {start: -10, stop: -5} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```

#### Example

```js
cov.subsetByValue({z: {target: -10} }).then(function(subsetCov) {
    // work with subsetted coverage
}
```
