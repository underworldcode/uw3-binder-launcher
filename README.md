# Underworld3 Binder Launcher

Launch Underworld3 tutorials in your browser via mybinder.org.

## Launch Options

| Branch | Underworld3 Branch | Launch |
|--------|-------------------|--------|
| `main` | `main` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main) |
| `uw3-release-candidate` | `uw3-release-candidate` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/uw3-release-candidate) |
| `development` | `development` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development) |

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
    ├── git pull underworld3 (branch set by UW3_BRANCH env var)
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
- A new underworld3 branch needs a launcher (create new branch here)

Code changes to Underworld3 are pulled automatically on each launch.

## Adding a new branch

1. Create a new branch in this repo: `git checkout -b <branch-name>`
2. Edit `.binder/Dockerfile` to set `ENV UW3_BRANCH=<underworld3-branch>`
3. Push: `git push origin <branch-name>`
