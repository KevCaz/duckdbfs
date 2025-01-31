# duckdbfs 0.0.2

* spatial data query support! See README.md

* The S3 interface supports `arrow`-compatible URI notation:
  - Alternate endpoints can now be passed like so 
    `s3://userid:secret_token@bucket-name?endpoint_override=data.ecoforecast.org`
  - Users can omit the use of `*` (match any file) or `**` 
    (recursive search) and just supply a path.  Recursive search is then
    assumed automatically.  Note: unlike `arrow`, this still supports the
    use of globs (`*`) elsewhere in the path, e.g. `s3://bucket/*/path`

* `duckdb_s3_config` gains argument `anonymous` allowing users to ignore existing
  AWS keys that may be set in environmental variables or AWS configuration files.
  This can also be passed as the username position in URI notation, e.g.
  `s3://anonymous@bucket_name`.  

* `open_dataset` drops use of `endpoint` as an argument.  Instead, alternative
  S3 endpoints can be set either by using the URI query notation or calling
  `duckdb_s3_config()` first.  Additionally, any arguments to `duckdb_s3_config()`,
  including `s3_endpoint`, can now be passed to `open_dataset` through the `...`.
  Note these settings will override any set by the URI notation.

# duckdbfs 0.0.1

* Initial release to CRAN
