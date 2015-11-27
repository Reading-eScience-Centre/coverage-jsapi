# Range objects

## Range properties

### .size

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) with axis name as key and axis size as value. Identical to axis size information in [`Domain.axes`](Domain.md).

### .dataType

A string identifying the data type of the non-null range values within `.values`. Can be `"float"`, `"integer"`, or `"string"`.

### .validMin

If defined, any number in `.values` is equal or greater than `.validMin`.

### .validMax

If defined, any number in `.values` is equal or lower than `.validMax`.

If `.values` has only missing values or `.dataType` is `"string"`, then `.validMin` and `.validMax` are not defined, otherwise both exist.

## Range methods

### .get(obj)

Returns a range value of type `.dataType` or `null` for the given axis indices.

#### Parameters

`obj` - An object where each key is an axis name and each value an axis value index.
        Missing axis indices are defaulted to 0.

#### Examples

```js
var range = ...
console.log(range.size) // 'x' => 10, 'y' => 50, 't' => 1
var val = arr.get({x: 5, y: 49, t: 0})
```
