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

## Large pnpm monorepos (Mend OOM mitigation)

pnpm 11 re-verifies every lockfile entry against supply-chain policies during `pnpm install`, which can OOM Mend Renovate runners (~3 GB) on large workspaces. Renovate-only mitigation uses `PNPM_CONFIG_TRUST_LOCKFILE=true` so CI and local installs still run the full check.

Mend blocks this env var in repo `renovate.json` unless the org allowlists it. Choose one:

1. **Per-repository (recommended)** — Mend platform admin sets `customEnvVariables` for the repo in Mend Developer Platform (no `allowedEnv` change, no repo env needed):

   ```json
   {
     "customEnvVariables": {
       "PNPM_CONFIG_TRUST_LOCKFILE": "true"
     }
   }
   ```

2. **Org allowlist** — Add `PNPM_CONFIG_TRUST_LOCKFILE` to the Mend org `allowedEnv`, then extend `github>smg-automotive/renovate-config:pnpmLargeMonorepo` in the repo `renovate.json`.

## Excluding default settings

If the configuration does not fit your project, you can exclude certain presets by adding:

````json
{
  "ignorePresets": [
    "github>smg-automotive/renovate-config:groupLtsNodeVersions"
  ]
}
````
