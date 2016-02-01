# CoverageCollectionPaging objects

## CoverageCollectionPaging properties

### .total

The total number of coverages within the paged collection.

### .perPage

The number of coverages per page. The last page may have less than that.

## CoverageCollectionPaging methods

### .loadNext()

TODO what should this return? a collection object? or just coverages with paging info?

TODO what if we start not at the first page? should this be like an iterator? typically, that's needed in implementations. should we forbid coverage collections that start in the middle?
