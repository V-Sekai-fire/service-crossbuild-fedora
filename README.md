# service-crossbuild-fedora

A Fedora amd64 container, run with podman, that cross-builds scons projects for the `linux-amd64`, `windows-amd64` and `macos-*` targets.

## What it is for

One image carries every toolchain a desk needs to build the engine and its module checkouts for the three desktop targets, with a compiler cache that desks share when credentials for it are available. The `macos-*` toolchain is packaged once from an SDK archive you supply and published as a release asset, so later builds download it instead of rebuilding it.

## Build and run

```sh
scripts/build.sh <target> <project directory>
scripts/build-osxcross-package.sh <SDK archive>
```

The first builds a project with a top-level `SConstruct` for one target inside the container; the second packages and publishes the `macos-*` toolchain, once per SDK.

## Licence

MIT. See [LICENSE](LICENSE).
