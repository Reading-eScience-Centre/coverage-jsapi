# Parameter objects

## Parameter properties

### .key

A short alias of the Parameter, identical to the one used as key in [`Coverage.parameters`](Coverage.md#parameters).

### .dtype

The data type of the range values: `"number"` or `"string"`. Note that missing values are always represented as `null`. Boolean values should be represented as numbers together with the `.categories` property.

### .description

A textual, perhaps lengthy, description of the parameter.

### .observedProperty

An object with the properties `label` and optionally `id` and `description`. `label` is a short name of the observed property. If given, `id` is a URI that defines the property, and `description` is a, perhaps lengthy, textual description.

### .unit

An optionally defined object with the properties `symbol` and optionally `label`, both strings. If the `unit` property is not defined, then the parameter values are unitless. An example for `symbol` is "°C", and for `label` "Degrees Celsius".

### .categories

An optionally defined non-empty array of category objects. A category object has the `label` and `value` properties and may have `description` and `id` properties. The value of `label` is a short name of the category. The value of `value` is an integer unique within all category objects in `categories`. If given, the value of `id` is a URI and serves as common identifier. If given, the value of `description` is a textual description of the category.

Note that a parameter object cannot have both `unit` and `categories` properties.
