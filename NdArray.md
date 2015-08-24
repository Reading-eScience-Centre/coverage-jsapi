# NdArray objects

## NdArray properties

### .shape

The array shape as an array of integers.

## NdArray methods

### .get(i,j,...)

Returns the element `i,j,...` from the array, which is either a number or `null` (for missing data).

#### Parameters

`i,j,...` - Each parameter is an index for an array dimension.

#### Examples

```js
var arr = ...
console.log(arr.shape) // "[1,200,100]"
var val = arr.get(0,100,50)
```

### .lo(i,j,...)

Returns a subsetted NdArray view of this array with each dimension starting at the given indices.

#### Parameters

`i,j,...` - Each parameter is the start index for an array dimension. `null` is equal to 0.

### .hi(i,j,...)

Returns a subsetted NdArray view of this array with each dimension ending before the given indices.

#### Parameters

`i,j,...` - Each parameter is the end index (exclusive) for an array dimension. `null` is equal to the dimension size.

#### Examples

```js
var arr = ...
console.log(arr.shape) // [10,20,30]
var subset = arr.hi(null,10,10).lo(null,4,8) // compared to numpy: arr[:, 4:10, 8:10]
console.log(subset.shape) // [10,6,2]
```
