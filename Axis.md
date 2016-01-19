# Axis objects

Axis objects describe the values of a single domain axis.

## Axis properties

### .values

An [array](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array) or [typed array](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) of axis values. The size of the axis is equal to `.values.length`.

### .bounds

If defined, an array of axis value bounds of length `.values.length`. Each bound is a two-element array with lower and upper bound with the same type as the axis values themselves.
