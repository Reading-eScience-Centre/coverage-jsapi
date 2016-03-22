# CoverageCollectionQuery objects

A CoverageCollectionQuery object allows to build a query over a coverage collection via method chaining and execute the query.

## CoverageCollectionQuery methods

### .filter(constraints)

Filter coverages by domain values. Only those that satisfy the filter constraint are included in the resulting collection.

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

Only applies when the query is run against a server. Indicates a preference to the server to embed the domain and/or range data of all coverages in a single request. The server may not support or honor the preference. Note that this preference, whether fulfilled or not, has no influence on the JavaScript API.

#### Examples

```js
query.embed({ domain: true, range: true }).execute().then(function(coll) {
  // work with collection
})
```

### .execute()

Returns a [`Promise`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) that succeeds with a [`CoverageCollection`](CoverageCollection.md) object.
