# Underworld3 Binder Launcher

Launch Underworld3 in your browser via mybinder.org - either with the built-in tutorials or with your own content.

## Quick Launch (Underworld3 Tutorials)

Click to launch JupyterLab with Underworld3 tutorials:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-launcher/main)

## Launch Your Own Content

**Your repository needs NO special configuration!** Use the binder wizard to generate a launch badge:

```bash
# In the underworld3 repository
python scripts/binder_wizard.py
```

Or generate manually:
```
https://mybinder.org/v2/gh/underworldcode/uw3-launcher/main
  ?urlpath=git-pull
  ?repo=https://github.com/YOUR-USERNAME/YOUR-REPO
  &branch=main
  &urlpath=lab/tree/YOUR-REPO
```

### Example Badge for Your README

```markdown
[![Launch in Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-launcher/main?urlpath=git-pull%3Frepo%3Dhttps%253A%252F%252Fgithub.com%252FYOUR-USERNAME%252FYOUR-REPO%26branch%3Dmain%26urlpath%3Dlab%252Ftree%252FYOUR-REPO)
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Your Content Repository                              │
│                         (No .binder/ needed!)                                │
│                                                                              │
│   your-username/your-course                                                  │
│   ├── notebooks/                                                            │
│   │   ├── tutorial-1.ipynb                                                  │
│   │   └── tutorial-2.ipynb                                                  │
│   └── README.md  ← Just add a launch badge here!                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     │ Badge click
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            mybinder.org                                      │
│                                                                              │
│   1. Uses this launcher repo (cached, fast!)                                │
│   2. Pulls pre-built UW3 image from GHCR                                    │
│   3. nbgitpuller clones YOUR repo into workspace                            │
│   4. Opens JupyterLab with your notebooks                                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         JupyterLab Session                                   │
│                                                                              │
│   /home/jovyan/                                                             │
│   ├── underworld3/          (UW3 source + tutorials)                        │
│   └── your-course/          (YOUR cloned repository)                        │
│       └── notebooks/                                                        │
│                                                                              │
│   Kernel: Underworld3 (Python with UW3 + dependencies)                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Benefits

| Feature | Traditional Binder | This Launcher |
|---------|-------------------|---------------|
| Setup required | `.binder/` directory, Dockerfile | Nothing! |
| Build time | 10-20+ minutes | Instant (cached) |
| Cache invalidation | Any commit | Never (same image) |
| Dependencies | Must specify all | All included |
| Maintenance | Per-repository | Zero |

## Requirements for Your Repository

1. **Must be public** on GitHub
2. **Notebooks should use `python3` kernel** (not custom kernel names)
3. **Import Underworld3** as: `import underworld3 as uw`

That's it! No Dockerfile, no environment.yml, no requirements.txt needed.

## Launcher Branches

Different branches provide different UW3 versions:

| Launcher Branch | UW3 Branch | Purpose |
|-----------------|------------|---------|
| `main` | `main` | Stable release |
| `uw3-release-candidate` | `uw3-release-candidate` | Testing |
| `development` | `development` | Bleeding edge |

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

## Technical Details

This repository exists to provide a stable mybinder.org cache. The actual computation environment is pre-built and hosted on GitHub Container Registry (GHCR).

When dependencies change in Underworld3, we rebuild and push a new base image. This launcher repository only needs updating when the image tag changes.

### For Maintainers

To update the base image reference:
1. Edit `.binder/Dockerfile`
2. Change the `FROM` tag to the new image version
3. Push to trigger mybinder.org cache refresh
