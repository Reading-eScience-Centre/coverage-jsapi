# CoverageCollectionQuery objects

A CoverageCollectionQuery object allows to build a query over a coverage collection via method chaining and execute the query.

## CoverageCollectionQuery methods

### .filter(constraints)

#### Examples

```js
query.filter({
  't': {start: '2015-01-01T01:00:00', stop: '2015-01-01T02:00:00'}
}).execute().then(function(coll) {
  // work with filtered collection
})
```

### .subset(constraints)

Subset coverages by domain values.

Equivalent to calling [`Coverage.subsetByValue(constraints)`](Coverage.md) on each coverage in the collection.

#### Examples

```js
query.subset({
  't': '2015-01-01T01:00:00'
}).execute().then(function(coll) {
  // work with subsetted collection
})
```

### .embed(constraints)



#### Examples

```js
query.embed({ range: true }).execute().then(function(coll) {
  // work with collection
})
```

### .execute()

Returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) that succeeds with a [`CoverageCollection`](CoverageCollection.md) object.
