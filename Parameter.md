# Parameter objects

## Parameter properties

### .key

A short alias of the Parameter, identical to the one used as key in [`Coverage.parameters`](Coverage.md#parameters).

### .description

A [`LanguageMap`](LanguageMap.md) object with a textual, perhaps lengthy, description of the parameter.

### .observedProperty

An [`ObservedProperty`](ObservedProperty.md) object.

### .unit

An optionally defined object with the properties `symbol` and optionally `label`. `symbol` is an object with the properties `value` and optionally `type` where both are strings with `value` the unit string, for example `"°C"`, and `type` a URI identifying the coding scheme, for example `"http://www.opengis.net/def/uom/UCUM/"`. `label` is a [`LanguageMap`](LanguageMap.md) object, for example `{en: "Degrees Celsius"}`. If the `unit` property is not defined, then the parameter values are unitless.

### .categoryEncoding

An optionally defined [`Map`](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Map)
object where each key is a [`Category`](ObservedProperty.md) ID, and each value an array of integers where each integer is unique within this map.
This property is used to relate categories encoded as numbers in coverage [range values](Range.md) to their actual [`Category`](ObservedProperty.md).


Note that a parameter object cannot have both `unit` and `observedProperty.categories`/`categoryEncoding` properties.
