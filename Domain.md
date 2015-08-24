# Domain objects

Domain objects describe the coordinates and their ordering in a domain.
As part of this API, no common domain types are defined.
This allows for Coverage formats and implementations to evolve naturally and prevents settling on a fixed and potentially "wrong" set of domain types. Equally, it allows for unusual domain types that are only used in a specific area.

## Domain properties

### .type

A URI as identifier for the type of domain, e.g. "http://coveragejson.org/def#Grid", identical to the [`Coverage.type`](Coverage.md) property.
The type uniquely defines the .shape property, semantics of all axes, and further properties.

### .shape

The number of elements in each domain dimension given as an array of integers.
This is identical to the array shapes of all ranges.
