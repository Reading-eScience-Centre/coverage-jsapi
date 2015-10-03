# JavaScript API for [Coverage](https://en.wikipedia.org/wiki/Coverage_data) objects

A JavaScript API for handling arbitrary coverage data. The API is based on the object structure of [CoverageJSON](https://github.com/neothemachine/coveragejson) but abstracts over it to make it exchangeable. It's purpose is to serve as a common interface that libraries can implement and depend on. It is a work-in-progress and the API is likely to change in some areas.

Start here: [`Coverage` objects](Coverage.md)

## Implementations

- [covjson-reader](https://github.com/Reading-eScience-Centre/covjson-reader) - Library that reads CoverageJSON documents, exposing the data as [`Coverage` objects](Coverage.md)
- [leaflet-coverage](https://github.com/Reading-eScience-Centre/leaflet-coverage) - [Leaflet](http://leafletjs.com/) plugin that visualizes [`Coverage` objects](Coverage.md) on a map

## Acknowledgments

This specification is developed within the [MELODIES project](http://www.melodiesproject.eu).
