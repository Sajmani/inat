# inat

A Go (golang) iNaturalist client

## cfg.yaml

We generate the Go client using oapi-codegen as documented on https://github.com/oapi-codegen/oapi-codegen?tab=readme-ov-file#generating-api-clients

We configure the output options to use Go-style initialisms.

## api.json

Update api.json from https://api.inaturalist.org/v2/api-docs

Validate api.json as YAML using https://editor.swagger.io/

Manually fix line 16117 in pretty-printed api.json (as of Aug 11, 2025),
"in": "path" should be "in": "query" for the "include_ancestors" parameter
for the "/observations/species_counts" path.

