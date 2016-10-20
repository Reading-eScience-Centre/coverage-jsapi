# Domain objects

Domain objects describe the coordinates and their ordering in a domain.
As part of this API, no common domain types are defined.
This allows for Coverage formats and implementations to evolve naturally and prevents settling on a fixed and potentially "wrong" set of domain types. Equally, it allows for unusual domain types that are only used in a specific area.

## Domain properties

### .type

The constant `"Domain"`.

### .domainType

If defined, then the domain follows the given domain type, e.g. `'https://covjson.org/def/domainTypes#Trajectory'`.

### .axes

A [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map) containing information for all axes of this domain. Each key is an axis name and each value an [`Axis`](Axis.md) object.

### .referencing

An array of objects associating components to reference systems. Each object has a `"coordinates"` property and a `"system"` property. The `"coordinates"` property lists the identifiers of the coordinates for which the reference system applies (in correct order if relevant), while the `"system"` property is a reference system object. For now, reference system objects are exactly as defined in the [CoverageJSON](https://covjson.org/spec/#reference-system-objects) format.
