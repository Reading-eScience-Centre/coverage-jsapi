# Coverage objects

## Coverage properties

### .type

The type of the coverage, more specifically of its domain. One of `Grid`, ...

### .parameters



## Coverage methods

### .loadRange()

The `loadRange()` method returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which loads the requested range data and provides a [`Range`](Range.md) object in its callback.

#### Syntax

```js
cov.loadRange(paramId)
```

#### Parameters

`paramId` - The ID of the [`Parameter`](Parameter.md) for which to load the range

#### Examples

```js
var paramId = 'salinity'
cov.loadRange(paramId).then(function(range) {
  console.log(range.validMin, range.validMax)
  console.log(range.values)
})
```
