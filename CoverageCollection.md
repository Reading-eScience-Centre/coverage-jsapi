# CoverageCollection objects

## CoverageCollection properties

### .type

The constant `"CoverageCollection"`.

### .id

An optionally defined URI that serves as common identifier for this coverage collection.

### .domainType

If defined, every coverage in the collection has the given domain type. This is typically a URI.

### .coverages

An array of [`Coverage`](Coverage.md) objects.

### .parameters

If defined, an array of [`Parameter`](Parameter.md) objects. TODO describe invariants

### .paging

If defined, a [`CoverageCollectionPaging`](CoverageCollectionPaging.md) object. In this case the collection is paged and the current page corresponds to this `CoverageCollection` object. Remaining coverages may be loaded via methods of the [`CoverageCollectionPaging`](CoverageCollectionPaging.md) object.

## CoverageCollection methods

### .query()

Returns a [`CoverageCollectionQuery`](CoverageCollectionQuery.md) object with which this collection can be filtered, subsetted, etc.

#### Examples

```js
collection.query()
  .filter({
    't': {start: '2015-01-01T00:00:00', stop: '2015-01-01T12:00:00'}
  })
  .subset({
    'z': {start: 10, stop: 20}
  })
  .execute().then(function(newcollection) {
    console.log(newcollection.coverages.length)
  })
```
