# Parameter objects

## Parameter properties

### .key

A short alias of the Parameter, identical to the one used as key in [`Coverage.parameters`](Coverage.md#parameters).

### .description

A [`LanguageMap`](LanguageMap.md) object with a textual, perhaps lengthy, description of the parameter.

### .observedProperty

An object with the properties `label` and optionally `id` and `description`. `label` is a [`LanguageMap`](LanguageMap.md) object with a short name of the observed property. If given, `id` is a URI that defines the property, and `description` is a [`LanguageMap`](LanguageMap.md) object with a, perhaps lengthy, textual description.

### .unit

An optionally defined object with the properties `symbol` and optionally `label`. `symbol` is a string, while `label` is a [`LanguageMap`](LanguageMap.md) object. If the `unit` property is not defined, then the parameter values are unitless. An example for `symbol` is "°C", and for `label` "en"->"Degrees Celsius".

### .categories

An optionally defined non-empty array of category objects. A category object has the `label` and `values` properties and may have `description` and `id` properties. The value of `label` is a [`LanguageMap`](LanguageMap.md) object with a short name of the category. The value of `values` is an array of integers where each integer is unique within all category objects in `categories`. If given, the value of `id` is a URI and serves as common identifier. If given, the value of `description` is a [`LanguageMap`](LanguageMap.md) object with a textual description of the category.

Note that a parameter object cannot have both `unit` and `categories` properties.
