# JavaScript API for [Coverage](https://en.wikipedia.org/wiki/Coverage_data) objects

This is based on [CoverageJSON](https://github.com/neothemachine/coveragejson) but abstracts over it to make it exchangeable. It's purpose is to serve as a common interface that libraries can implement and depend on.

## Coverage properties

### .type

The type of the coverage, more specifically of its domain. One of `Grid`, ...

### .parameters



## Coverage methods

### .loadRange()

The `loadRange()` method returns a `Promise` object which loads the requested range data and provides a `Range` object in its callback.

#### Syntax

```js
cov.loadRange(paramId)
```

#### Parameters

`paramId` - The ID of the *parameter* for which to load the range

#### Examples

```js
var paramId = 'salinity'
cov.loadRange(paramId).then(function(range) {
  console.log(range.validMin, range.validMax)
  console.log(range.values)
})
```
