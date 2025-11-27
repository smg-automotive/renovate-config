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

Our configuration pins all dependencies (dev and regular) to a specific version.

For a web project add `github>smg-automotive/renovate-config:web` to renovate.json.
For a package add `github>smg-automotive/renovate-config:pkg` to renovate.json.

````json
{
  "extends": [
    "github>smg-automotive/renovate-config",
    "github>smg-automotive/renovate-config:web"
  ]
}
````

With that, we are following the [recommendation](https://docs.renovatebot.com/dependency-pinning/#so-whats-best) from renovate.

## Excluding default settings

If the configuration does not fit your project, you can exclude certain presets by adding:

````json
{
  "ignorePresets": [
    "github>smg-automotive/renovate-config:groupLtsNodeVersions"
  ]
}
````
