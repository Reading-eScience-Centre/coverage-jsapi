# Domain objects

Domain objects describe the coordinates and their ordering in a domain.
As part of this API, no common domain types are defined.
This allows for Coverage formats and implementations to evolve naturally and prevents settling on a fixed and potentially "wrong" set of domain types. Equally, it allows for unusual domain types that are only used in a specific area.

## Domain properties

### .type

A URI as identifier for the type of domain, e.g. "http://coveragejson.org/def#Grid", identical to the [`Coverage.domainType`](Coverage.md) property.

### .size

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) containing size information for all axes of this domain. Each key is an axis name and each value the axis size (number of axis values). See also [`Coverage.subsetByIndex`](Coverage.md#subsetbyindexconstraints).
