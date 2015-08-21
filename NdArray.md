# NdArray objects

## NdArray properties

### .shape

The array shape as an array of integers.

## NdArray methods

### .get(i,j,...)

Returns the element `i,j,...` from the array, which is either a number, string, boolean, or `null` (for missing data). The value type is the same for all elements and is equal to the associated [`Parameter`](Parameter.md)'s dtype property.

#### Parameters

`i,j,...` - Each parameter is an index for an array dimension.

#### Examples

```js
var arr = ...
console.log(arr.shape) // "[1,200,100]"
var val = arr.get(0,100,50)
```
