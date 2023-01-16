# vcpkg-build

[![CI](https://github.com/dartsim/vcpkg-build/workflows/CI/badge.svg)](https://github.com/dartsim/vcpkg-build/actions)

## Overview

This repository publishes archives of [vcpkg] with the [DART] dependencies installed.

The installed vcpkg packages are different by the DART versions. Please check [.github/workflows/ci.yml](.github/workflows/ci.yml) for the details.

To download the archives,

```shell
# Install wget if not already
choco install -y wget

# Download the archive (see to check available <tag>: https://github.com/dartsim/vcpkg-build/releases)
wget -q https://github.com/dartsim/vcpkg-build/releases/download/<tag>/<zip_name>.zip

# Extract the vcpkg files
unzip -qq <zip_name>.zip -d <path>
```

The available `<zip_name>`s are:

- `vcpkg-dartsim-deps-v6.13`
- `vcpkg-dartsim-deps-v7.0`
- `vcpkg-dartsim-deps-min-v7.0`
- `vcpkg-dartsim-deps-cuda-v7.0`
- `vcpkg-dartsim-deps-v8.0`
- `vcpkg-dartsim-deps-cuda-v8.0`

## Release Process

1. Get a vcpkg commit or tag that you want to use from [vcpkg] (e.g., `70f192e`).
1. Update [`VCPKG_VERSION`](https://github.com/dartsim/vcpkg-build/blob/9525f91281fb0151939eaa9ebd0eb6182f230474/.github/workflows/ci.yml#L18) in `ci.yaml` to the vcpkg commit or tag
1. Push the change to this repository
1. Create a tag for the change in the pattern of `<this_repo_version>-<vcpkg_commit_or_tag>` (e.g., `v0.2.0-70f192e`)
1. Create a release from the tag, then GitHub Actions will publish a new vcpkg archive that can be found in the Assets section in the [Release page](https://github.com/dartsim/vcpkg-build/releases).

[dart]: https://github.com/dartsim/dart
[vcpkg]: https://github.com/microsoft/vcpkg
