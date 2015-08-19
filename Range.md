# Range objects

## Range properties

### .values

An [`NdArray`](NdArray.md) object with shape and element ordering as defined by the domain.

### .validMin

If defined, any number in .values is equal or greater than .validMin.

### .validMax

If defined, any number in .values is equal or lower than .validMax.

Note that either none or both validMin/validMax are defined.
