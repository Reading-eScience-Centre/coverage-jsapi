# Example: GPX tracks with Garmin TrackPoint Extensions

The [GPX format](https://en.wikipedia.org/wiki/GPS_Exchange_Format) is used for
storing waypoint/route/track geo data, mostly linked to GPS devices.
A track is the actually traveled path that was followed, as recorded by a GPS device,
containing track points with data such as GPS accuracy.
A route is the planned path, containing route points with data such as name or comments.
A waypoint is a marker with a label (and other data) used for orientation/reference.

Garmin developed extensions for use with track points to store additional information:
- [temperature, depth, heart rate, cadence](http://www8.garmin.com/xmlschemas/TrackPointExtensionv1.xsd)
- [x, y, z acceleration](http://www8.garmin.com/xmlschemas/AccelerationExtensionv1.xsd)

We focus on the track data here since this is what is most suitable for interpretation
as a Coverage.

## Mapping specifics

A track corresponds to what we call "Trajectory" Domain. 
Each of the track point extension types (like heart rate) is a Parameter.
The set of values for one extension type is then a Range.

TODO add more details
