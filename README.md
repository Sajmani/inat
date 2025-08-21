# inat

A Go (golang) iNaturalist client

## cfg.yaml

We generate the Go client using oapi-codegen as documented on https://github.com/oapi-codegen/oapi-codegen?tab=readme-ov-file#generating-api-clients

We configure the output options to use Go-style initialisms
and inline struct fields, rather than pointers.

## api.json

Update api.json from https://api.inaturalist.org/v2/api-docs

Validate api.json as YAML using https://editor.swagger.io/

Manual fixes as of Aug 20, 2025:

Manually fix two occurrences of `observation_field_values_attributes` to have an array type:
```
"observation_field_values_attributes": {
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "observation_field_id": {
        "type": "integer"
      },
      "value": {}
    },
    "required": [
      "observation_field_id",
      "value"
    ],
    "additionalProperties": false
  }
},
```

Specify Go type names for nested messages:
```
      "ObservationsCreate": {
        "type": "object",
        "properties": {
          "fields": {

          },
          "observation": {
            "type": "object",
            "x-go-type-name": "ObservationCreate",
```
```
      "ObservationsUpdate": {
        "type": "object",
        "properties": {
          "fields": {

          },
          "ignore_photos": {
            "type": "boolean"
          },
          "observation": {
            "type": "object",
            "x-go-type-name": "ObservationUpdate",
```
In two places:
```
              "observation_field_values_attributes": {
                "type": "array",
                "items": {
                  "type": "object",
                  "x-go-type-name": "ObservationFieldValueAttribute",
```
