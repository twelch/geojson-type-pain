Suggestion:
* All library geojson types should implement hard spec requirements (MUST/MUST NOT/REQUIRED/SHALL/SHALL NOT).
* All libraries should clearly document when they choose positions/options that are not required (SHOULD/SHOULD NOT, RECOMMENDED/NOT RECOMMENDED) and why it's useful to this particular library. "Ease of use" is not necessarily a good enough reason if it's trading ease of implementation within the library, at the cost of ease of integration between libraries.
* In practice, types can be implemented differently but still meet the spec.  This can cause cause friction/incompatibility.  Maintainers should strive to be compatible and if one can't be demonstrated as measurably better than the other, one should just be picked.

Sharing types:
* due to convenience geojson Definitely Typed (aka geojsonDT) has become a commonly used library for geojson types for the whole spec.  It's for convenience that people grab `@types/geojson`.  There's nothing saying it should be the source of truth.  It's counterpart NPM library `geojson.js` doesn't do much.