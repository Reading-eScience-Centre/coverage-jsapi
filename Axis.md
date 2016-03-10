# Axis objects

Axis objects describe the values of a single domain axis.

## Axis properties

### .dataType

A URI describing the structure of the axis values, e.g. http://coveragejson.org/def#Tuple or http://coveragejson.org/def#Polygon. If undefined, then the axis values are assumed to be primitive (numbers or strings).

### .components

An array of component identifier strings where the order of components is defined by the data type. Each axis value can be referenced within the given components using reference systems (see [Domain](Domain.md)). If the axis has only a single component, then the component identifier is guaranteed to be equal to the axis identifier.

### .values

An [array](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array) or [typed array](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) of axis values. The size of the axis is equal to `.values.length`.

### .bounds

If defined, an array of axis value bounds of length `.values.length`. Each bound is a two-element array with lower and upper bound with the same data type as the axis values themselves.
