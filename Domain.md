# Domain objects

Domain objects describe the coordinates and their ordering in a domain.
As part of this API, no common domain types are defined.

## Domain properties

### .type

A URI as identifier for the type of domain, e.g. "http://coveragejson.org/def/domains/Grid".
The type uniquely defines the .shape property array elements, semantics of all axes, and further properties.

### .shape

The number of elements in each domain dimension given as an array of integers.
This is identical to the array shapes of all ranges.
