# ObservedProperty objects

## ObservedProperty properties

### .id

An optionally defined URI that serves as common identifier.

### .label

A [`LanguageMap`](LanguageMap.md) object with a short name of the observed property.

### .description

A [`LanguageMap`](LanguageMap.md) object with a textual, perhaps lengthy, description of the observed property.

### .categories

An optionally defined non-empty array of category objects. A category object has the `label` and `id` properties and may have a `description`  property. The value of `label` is a [`LanguageMap`](LanguageMap.md) object with a short name of the category. The value of `id` is a URI and serves as common identifier. If given, the value of `description` is a [`LanguageMap`](LanguageMap.md) object with a textual description of the category.
