# NdArray objects

## NdArray properties

### .shape

The array shape as an array of integers.

## NdArray methods

### .get(i,j,...)

Returns the element `i,j,...` from the array, which is either a number, a string, or `null` (for missing data).

#### Parameters

`i,j,...` - Each parameter is an index for an array dimension.

#### Examples

```js
var arr = ...
console.log(arr.shape) // "[1,200,100]"
var val = arr.get(0,100,50)
```
