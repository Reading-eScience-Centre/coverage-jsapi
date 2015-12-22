# JavaScript API for [Coverage Data](https://en.wikipedia.org/wiki/Coverage_data)

A JavaScript API for handling arbitrary coverage data. The API is based on the object structure of [CoverageJSON](https://github.com/neothemachine/coveragejson) but abstracts over it to make it exchangeable. It's purpose is to serve as a common interface that libraries can implement and depend on. It is a work-in-progress and the API is likely to change in some areas.

Start here: [`Coverage` objects](Coverage.md) or [`CoverageCollection` objects](CoverageCollection.md)

## Implementations

- [covjson-reader](https://github.com/Reading-eScience-Centre/covjson-reader) - Library that reads CoverageJSON documents, exposing the data as [`Coverage`](Coverage.md) or [`CoverageCollection`](CoverageCollection.md) objects
- [coverage-rest-client](https://github.com/Reading-eScience-Centre/coverage-rest-client) - Library that wraps [`Coverage` objects](Coverage.md) and runs operations like subsetting server-side (support for [`CoverageCollection`](CoverageCollection.md) objects will follow)
- [leaflet-coverage](https://github.com/Reading-eScience-Centre/leaflet-coverage) - [Leaflet](http://leafletjs.com/) plugin that visualizes [`Coverage` objects](Coverage.md) on a map (support for [`CoverageCollection`](CoverageCollection.md) objects will follow)

## Acknowledgments

This specification is developed within the [MELODIES project](http://www.melodiesproject.eu).
