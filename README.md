# JavaScript API for [Coverage Data](https://en.wikipedia.org/wiki/Coverage_data)

A JavaScript API for handling arbitrary coverage data. The API is based on the object structure of [CoverageJSON](https://covjson.org) but abstracts over it to make it exchangeable. It's purpose is to serve as a common interface that libraries can implement and depend on. It is a work-in-progress and the API is likely to change in some areas.

Start here: [`Coverage` objects](Coverage.md) or [`CoverageCollection` objects](CoverageCollection.md)

## Implementations

- [covjson-reader](https://github.com/Reading-eScience-Centre/covjson-reader) - Library that reads CoverageJSON documents, exposing the data as [`Domain`](Domain.md), [`Coverage`](Coverage.md), or [`CoverageCollection`](CoverageCollection.md) objects
- [leaflet-coverage](https://github.com/Reading-eScience-Centre/leaflet-coverage) - [Leaflet](http://leafletjs.com/) plugin that visualizes [`Domain`](Domain.md), [`Coverage`](Coverage.md), and [`CoverageCollection`](CoverageCollection.md) objects on a map

## Acknowledgments

This specification is developed within the [MELODIES project](http://www.melodiesproject.eu).
