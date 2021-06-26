```csharp
public class Trip : GTFSIdentifiedEntity
```

# Summary
Defines a single trip of a transit route within a GTFS feed.

- [Summary](#summary)
- [Constructors](#constructors)
  - [`GTFSIdentifiedEntity(GTFSPropertyCollection, string)` (protected)](#gtfsidentifiedentitygtfspropertycollection-string-protected)
- [Properties](#properties)
  - [`BikesAllowed`](#bikesallowed)
  - [`BlockId`](#blockid)
  - [`DirectionId`](#directionid)
  - [`Headsign`](#headsign)
  - [`ID`](#id)
  - [`RouteId`](#routeid)
  - [`ServiceId`](#serviceid)
  - [`ShapeId`](#shapeid)
  - [`ShortName`](#shortname)
  - [`this[string]`](#thisstring)
  - [`WheelchairAccessible`](#wheelchairaccessible)
  - [`Properties` (protected)](#properties-protected)
- [Methods](#methods)
  - [`Factory(IEnumerable<(string, string)>)` (static)](#factoryienumerablestring-string-static)



# Constructors


## `GTFSIdentifiedEntity(GTFSPropertyCollection, string)` (protected)
Creates a `GTFSIdentifiedEntity`.

### Parameters
* `GTFSPropertyCollection` **`properties`**: The entity's collection of properties.
* `string` **`idName`**: The key of the property that identifies this entity.



# Properties


## `BikesAllowed`
Read-only `Tristate`: Indicates whether or not bikes are allowed on the trip.

This is the value of the `bikes_allowed` property of the entity, which defaults to `Tristate.Unknown`. 


## `BlockId`
Read-only `string`: Identifies the block to which the trip belongs.

This is the value of the `block_id` property of the entity. A block consists of a single trip or many sequential trips made using the same vehicle, defined by shared service days and `BlockId`. A `BlockId` can have trips with different service days, making distinct blocks.


## `DirectionId`
Read-only `DirectionId?`: Indicates the direction of travel for a trip.

This is the value of the `direction_id` property of the entity. This field is not used in routing; it provides a way to separate trips by direction when publishing time tables.

For example: The `trip_headsign` and `direction_id` fields could be used together to assign a name to travel in each direction for a set of trips. A trips.txt file could contain these records for use in time tables:

```csv
trip_id,...,trip_headsign,direction_id
1234,...,Airport,0
1505,...,Downtown,1
```

## `Headsign`
Read-only `string`: Text that appears on signage identifying the trip's destination to riders.

This is the value of the `trip_headsign` property of the entity. Use this field to distinguish between different patterns of service on the same route. If the headsign changes during a trip, `Headsign` can be overridden by specifying values for `StopTimes.Headsign`.


## `ID`
Read-only `string`: The ID of the entity.

This is the value of the `trip_id` property of the entity.


## `RouteId`
Read-only `string`: Identifies the route to which this trip belongs.

This is the value of the `route_id` property of the entity.


## `ServiceId`
Read-only `string`: Identifies the set of days on which this trip runs.

This is the value of the `service_id` property of the entity.


## `ShapeId`
Read-only `string`: Identifies a geospatial shape that describes the vehicle travel path for a trip.

This is the value of the `shape_id` property of the entity, and is required if the trip has continuous behavior defined, either at the route level or at the stop time level.


## `ShortName`
Read-only `string`: Public facing text used to identify the trip to riders, for instance, to identify train numbers for commuter rail trips.

This is the value of the `trip_short_name` property of the entity. If riders do not commonly rely on trip names, this field should be empty. A `ShortName` value, if provided, should uniquely identify a trip within a service day; it should not be used for destination names or limited/express designations.


## `this[string]`
Read-only `string`: Returns the given property of this entty, or `null` if no such property exists.


## `WheelchairAccessible`
Read-only `Tristate`: Indicates whether or not the trip is wheelchair accessible.

This is the value of the `wheelchair_accessible` property
of the entity, which defaults to `Tristate.Unknown`.


## `Properties` (protected)
`GTFSPropertyCollection`: The raw view of the properties of this entity.



# Methods


## `Factory(IEnumerable<(string, string)>)` (static)
`Trip`: Creates a new `Trip`.

### Parameters
* `IEnumerable<(string, string)>` **`properties`**: The property collection.