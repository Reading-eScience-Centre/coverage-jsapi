# Example: CoverageJSON

There is more or less a 1-to-1 relationship between the fields and/or concepts or both.
A CoverageJSON Coverage becomes a Coverage object, and a collection becomes multiple Coverage objects.
CoverageJSON range or domain documents cannot be mapped to Coverage objects.

## Specifics for Mapping

### type

The `type` property of a CoverageJSON Coverage has a name like "GridCoverage" where there 
is a 1-to-1 relation to the domain type, in that case "Grid". Since the domain may not
be embedded, the domain type has to be extracted from the coverage type. This means
cutting of the "Coverage" suffix and prepending the first part of the URL which is
contained in the JSON-LD context: "http://coveragejson.org/def#".

### Parameters in collections

In CoverageJSON CoverageCollection documents, the parameters of the coverages can be
moved into the root to avoid redundancy. Since there is no concept of a collection
in the Coverage Javascript API, these Parameters have to be exposed in each
Coverage object.

### Range values

CoverageJSON range values can be stored with an offset/factor and/or missing value encoding.
Such encoded range values have to be decoded when exposing them in a Coverage object of this API.
