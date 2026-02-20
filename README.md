# Underworld3 Binder Launcher

Launch Underworld3 in your browser via mybinder.org - either with the built-in tutorials or with your own content.

## Quick Launch (Underworld3 Tutorials)

Click to launch JupyterLab with Underworld3 tutorials:

| Launcher Branch | UW3 Branch | Launch |
|-----------------|------------|--------|
| `main` | `main` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main) |
| `development` | `development` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development) |

## Launch Your Own Content

**Your repository needs NO special configuration!** Use the binder wizard to generate a launch badge:

```bash
# In the underworld3 repository
python scripts/binder_wizard.py
```

## How It Works

This repository exists to provide a stable mybinder.org cache. The actual computation environment is pre-built and hosted on GitHub Container Registry (GHCR).

## What's Included

The pre-built environment includes:
- **Underworld3** with all dependencies
- **PETSc** for parallel solvers
- **gmsh** for mesh generation
- **PyVista** for visualization (trame backend)
- **JupyterLab** with Underworld3 kernel
- **nbgitpuller** for cloning your content
- **JIT compilation** toolchain for custom extensions

## Links

- **Underworld3**: https://github.com/underworldcode/underworld3
- **Documentation**: https://underworldcode.github.io/underworld3/
- **Badge Generator**: https://github.com/underworldcode/underworld3/blob/main/scripts/binder_wizard.py
- **Base Image**: https://github.com/underworldcode/underworld3/pkgs/container/uw3-base

### For Maintainers

To update the base image reference:
1. Edit `.binder/Dockerfile`
2. Change the `FROM` tag to the new image version
3. Push to trigger mybinder.org cache refresh
