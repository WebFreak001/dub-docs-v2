# The Recipe (dub.json / dub.sdl)

## Formats

TODO: [JSON](https://www.json.org/json-en.html) and [SDLang](https://sdlang.org) format.

You can convert between the available formats using [`dub convert`](../cli-reference/dub-convert.md).

## Reference

### Global settings

TODO: <https://dub.pm/package-format-json#standard-settings>

note to editors: probably want a separate sub-page for these things, to not push build settings and the other content too much down.

### Build settings

Build settings influence the command line options passed to the compiler and linker. Many settings support [platform specifications](./platform_specifications.md) to only apply the settings on certain targets. Most settings can also be overridden per configuration or build-type.

For available members, see [Build settings](../dub-reference/build_settings.md)

#### Environment variables

It is possible to use environment variables inside of build setting values using dollar notation. Refer to [Environment Variables](../dub-reference/environment_variables.md) for more details.

### Build types

Can specify a set of build setting overrides using `--build=XYZ`. Some default build types exist.

For available members and default build types, see [Build types](../dub-reference/buildtypes.md)

### Configurations

Can specify a set of build setting overrides using `--config=XYZ`. If no configurations are specified, some auto-generated ones exist.

For available members and auto-generated fallback configurations, see [Configurations](../dub-reference/configurations.md)

### Toolchain requirements

The package can specify version requirements for the toolchain. Each requirement is specified with the [version dependency syntax](../dub-reference/dependencies.md). For compilers, the keyword `no` can be specified instead of a version requirement to disallow the use of a specific compiler for the package. The following requirements are allowed:

| Identifier | Description |
| ---------- | ----------- |
| `"dub"`    | DUB version requirement |
|`"frontend"`| D frontend version requirement (equivalent to DMD version, applies to all compilers) |
| `"dmd"`    | DMD version requirement |
| `"ldc"`    | LDC version requirement |
| `"gdc"`    | GDC version requirement |

=== "dub.sdl"

    Example 1: package that needs at least dub v1.14 and uses D features introduced in frontend 2.068 (since DMD version 2.068) and other features that will be deprecated in frontend 2.087

    ```sdl
    toolchainRequirements dub=">=1.14.0" frontend=">=2.068 <2.087"
    ```

    Example 2: package that needs to be compiled with LDC from version 1.11

    ```sdl
    toolchainRequirements dmd="no" gdc="no" ldc=">=1.11.0"
    ```

=== "dub.json"

    Example 1: package that needs at least dub v1.14 and uses D features introduced in frontend 2.068 (since DMD version 2.068) and other features that will be deprecated in frontend 2.087

    ```json
    {
        "toolchainRequirements": {
            "dub": ">=1.14.0",
            "frontend": ">=2.068 <2.087"
        }
    }
    ```

    Example 2: package that needs to be compiled with LDC from version 1.11

    ```json
    {
        "toolchainRequirements": {
            "dmd": "no",
            "gdc": "no",
            "ldc": ">=1.11"
        }
    }
    ```
