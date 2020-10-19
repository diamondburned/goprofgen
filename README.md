# goprofgen

A shell script to generate a short `profile.go` file which starts a HTTP
listener for http://127.0.0.1:48574/debug/pprof.

## Installation

Dependencies: `cat`, `bash` (v4.4+ tested).

## Usage

```sh
# Generate a profile.go
goprofgen
# Delete the profile.go
goprofgen d # or delete
# Print a short help message
goprofgen h # or help
```

### Package Name Parsing

This script assumes package names to follow [Go's idiomatic package naming
convention][package-names], which mostly follows the regular expression
`[a-z]+`.

[package-names]: https://blog.golang.org/package-names

### Generating

All `profile.go` files generated will include a code generation header.
`goprofgen` will not try to override existing `profile.go` files (including
files it wrote by itself) and will instead error out.

### Deleting

`goprofgen` will check the `profile.go` file for the generated header before it
tries to remove the file. If no headers are found, it will error out.
