# CoverageCollectionPaging objects

## CoverageCollectionPaging properties

### .total

The total number of coverages within the paged collection.

### .hasPrevious

True if there is a page preceding this one.

### .hasNext

True if there is a page following this one.

## CoverageCollectionPaging methods

### .loadNext()

Returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`CoverageCollection`](CoverageCollection.md) object corresponding to the next collection page. If `.hasNext` is not true, then this method will raise an exception.

### .loadPrevious()

Returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`CoverageCollection`](CoverageCollection.md) object corresponding to the previous collection page. If `.hasPrevious` is not true, then this method will raise an exception.
