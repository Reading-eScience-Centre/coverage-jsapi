# [WaterML2](http://www.waterml2.org) time series

The [WaterML2 spec](https://portal.opengeospatial.org/files/?artifact_id=48531) details 
how water-related time series measurements can be serialized as XML.
It supports an interleaved and a domain-range encoding.

## Mapping specifics

### Point metadata (9.15.3)

Metadata can be recorded for each measurement point, e.g. accuracy, aggregationDuration, interpolationType.
If this is constant for all points, it can also be recorded once in a ´wml2:DefaultTVPMeasurementMetadata´
element.

TODO 

### Procedures

TODO is this part of the Coverage API? or is it custom metadata?
