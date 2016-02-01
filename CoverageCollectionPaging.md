# CoverageCollectionPaging objects

## CoverageCollectionPaging properties

### .total

The total number of coverages within the paged collection.

### .next

If defined, an object with a single method `load()` that when called returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`CoverageCollection`](CoverageCollection.md) object corresponding to the next collection page.

#### Example

```js
var coll = ...
if (coll.paging && coll.paging.next) {
  coll.paging.next.load().then(function (nextcoll) {
    // access coverages of next page
  })
)
```

### .previous

If defined, an object with a single method `load()` that when called returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) object which succeeds with a [`CoverageCollection`](CoverageCollection.md) object corresponding to the previous collection page.
