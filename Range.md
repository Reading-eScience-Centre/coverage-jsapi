# Range objects

## Range properties

### .values

An [`NdArray`](NdArray.md) object with shape and element ordering as defined by the domain.

### .dataType

A string identifying the data type of the non-null values within `.values`. Can be `"float"`, `"integer"`, or `"string"`.

### .validMin

If defined, any number in `.values` is equal or greater than `.validMin`.

### .validMax

If defined, any number in `.values` is equal or lower than `.validMax`.

If `.values` has only missing values or `.dataType` is `"string"`, then `.validMin` and `.validMax` are not defined, otherwise both exist.
