**Nested GeometryCollection**

The spec says:
```
To maximize interoperability, implementations SHOULD avoid nested
   GeometryCollections.
```
Interpretation: it's allowed, but not recommended.

turf doesn't support it:
```
export interface GeometryCollection extends GeometryObject {
  type: "GeometryCollection";
  geometries: Array<
    Point | LineString | Polygon | MultiPoint | MultiLineString | MultiPolygon
  >;
}
```

geojsonDT does support it:
```
type Geometry = Point | MultiPoint | LineString | MultiLineString | Polygon | MultiPolygon | GeometryCollection;
```
```
export interface GeometryCollection extends GeoJsonObject {
    type: "GeometryCollection";
    geometries: Geometry[];
}
```

Conclusion: ?

**Null feature geometry**

The spec says:
```
The value of the geometry member SHALL be either a Geometry object as defined above or, in the case that the Feature is unlocated, a JSON null value.
```

Turf doesn't allow.  Perhaps because Turf JS code in practice doesn't account for null either?
```
export interface Feature<G = Geometry | GeometryCollection, P = Properties> extends GeoJSONObject {
```
geojson does:
```
export interface Feature<G extends Geometry | null = Geometry, P = GeoJsonProperties> extends GeoJsonObject {
```

Conclusion: since it's required turf should support it.  Yes it's probably very rare to have a Feature with a null Geometry, and supporting will cause runtime check that it's not null.

