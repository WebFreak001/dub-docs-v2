# Dependency syntax

## `version`

See [version specifiers](./build_settings#version-specifiers).

* `version=""*""`
* `version="~>a.b.c"`
* `version="~>a.b"`
* `version=">=a"`
* `version=">=a <b"`
* `version="<b"`

|                            | (no release) | v0.0.1 | v0.1.0 | v0.2.0 | v1.0.0 | v2.0.0 |
|----------------------------|--------------|--------|--------|--------|--------|--------|
| `version="*"`              | ✓            | ✓      | ✓      | ✓      | ✓      | ✓      |
| `version="~>0.1.0"`        |              |        | ✓      |        |        |        |
| `version="~>0.1"`          |              |        | ✓      | ✓      |        |        |
| `version=">=0.1.0"`        |              |        | ✓      | ✓      | ✓      | ✓      |
| `version=">=0.1.0 <1.0.0"` |              |        | ✓      | ✓      |        |        |
| `version="<2.0.0"`         |              | ✓      | ✓      | ✓      | ✓      |        |

## `version` + `optional`
## `version` + `optional` + `default=false`
## `path`

Note: this is best used in sub-packages, avoid going outside of repository bounds for public projects.

## `repository`
### Git repostiories
## `dflags`
## `dub.selections.json`
## `dub add-path`
## `dub add-local`
## dependency/version resolution
## per-configuration dependencies
## `Have_xyz`
