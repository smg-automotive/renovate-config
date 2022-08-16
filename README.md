# renovate-config

A sharable config preset for renovate used by SMG automotive.

## Setup

Enable Renovate in your repository and create a `renovate.json` file in the root of your project:

````json
{
  "extends": [
    "github>smg-automotive/renovate-config"
  ]
}
````

By default, renovate will pin all **dev** dependencies and uses SemVer ranges for the others. If you work on a project that
is **not** `required()` by any other package, add `:pinDependencies` to renovate.json.

````json
{
  "extends": [
    "github>smg-automotive/renovate-config",
    ":pinDependencies"
  ]
}
````

## Excluding default settings
If the configuration does not fit your project, you can exclude certain presets by adding:

````json
{
  "ignorePresets": ["github>smg-automotive/renovate-config:autoMergeNonMajorNode"]
}
````
