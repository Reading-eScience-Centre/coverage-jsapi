# Range objects

## Range properties

### .values

An [`NdArray`](NdArray.md) object with shape and element ordering as defined by the domain.

### .validMin

If defined, any number in .values is equal or greater than .validMin.

### .validMax

If defined, any number in .values is equal or lower than .validMax.

If .values has only missing values, then .validMin and .validMax are not defined, otherwise both exist.
