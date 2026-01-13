# Underworld3 Binder Launcher

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main)

Launch Underworld3 tutorials in your browser via mybinder.org.

## How it works

This minimal repository exists to provide a stable mybinder.org cache. The actual Underworld3 code is pulled fresh on each launch.

**Architecture:**
```
mybinder.org
    │
    ├── Pulls pre-built image from GHCR
    │   ghcr.io/underworldcode/uw3-base:2025.01
    │
    └── Caches by this repo's commit hash
        (rarely changes → fast launches)

On container start:
    │
    ├── git pull latest underworld3
    ├── Rebuild (~30 seconds)
    └── Launch JupyterLab with tutorials
```

## Links

- **Underworld3 repository**: https://github.com/underworldcode/underworld3
- **Documentation**: https://underworldcode.github.io/underworld3/
- **Base image**: https://github.com/underworldcode/underworld3/pkgs/container/uw3-base

## Updating

This repo only needs updating when:
- The base image version changes (update `FROM` tag in `.binder/Dockerfile`)
- The base image URL changes

Code changes to Underworld3 are pulled automatically on each launch.
