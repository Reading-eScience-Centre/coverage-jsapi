# CoverageCollection objects

## CoverageCollection properties

### .id

An optionally defined URI that serves as common identifier for this coverage collection.

### .profiles

An array of URIs that characterize the collection further in the sense of [RFC6909](https://www.ietf.org/rfc/rfc6906.txt), e.g. `['http://coveragejson.org/def#TrajectoryCoverageCollection']`.

### .coverages

An array of [`Coverage`](Coverage.md) objects.

### .parameters

If defined, an array of [`Parameter`](Parameter.md) objects. TODO describe invariants

### .domainTemplate

If defined, a [`Domain`](Domain.md) object with zero domain values.
Every coverage in the collection has a domain that follows this template, except for its domain values.

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
  .embed({range: true})
  .execute().then(function(newcollection) {
    console.log(newcollection.coverages.length)
  })
```
