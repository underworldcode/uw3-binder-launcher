# Underworld3 Binder Launcher

Launch Underworld3 in your browser via [mybinder.org](https://mybinder.org) - no installation required.

## Quick Launch

| Branch | Underworld3 Branch | Launch |
|--------|-------------------|--------|
| `main` | `main` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main) |
| `development` | `development` | [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development) |

Click a badge above to launch JupyterLab with the Underworld3 tutorials.

## Launch Your Own Notebooks

This launcher supports **any public GitHub repository** via [nbgitpuller](https://nbgitpuller.readthedocs.io/). Your repository doesn't need a `.binder/` directory, Dockerfile, or any special configuration.

### URL Format

```
https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/<uw3-branch>
  ?urlpath=git-pull
    %3Frepo%3D<your-repo-url-encoded>
    %26branch%3D<your-branch>
    %26urlpath%3Dlab%2Ftree%2F<repo-name>%2F<path-to-notebook>
```

### Parameters

| Parameter | Description | Example |
|-----------|-------------|---------|
| `<uw3-branch>` | Which Underworld3 branch to use | `development`, `main` |
| `repo` | Your GitHub repository URL (URL-encoded) | `https%3A%2F%2Fgithub.com%2Fuser%2Frepo` |
| `branch` | Branch of your repository to clone | `main` |
| `urlpath` | Where to open in JupyterLab | `lab/tree/repo-name/notebook.ipynb` |

### Example: Launch a Course Repository

To launch `myuser/geodynamics-course` (branch `main`) using the `development` branch of Underworld3, opening `tutorials/intro.ipynb`:

```
https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development?urlpath=git-pull%3Frepo%3Dhttps%253A%252F%252Fgithub.com%252Fmyuser%252Fgeodynamics-course%26branch%3Dmain%26urlpath%3Dlab%252Ftree%252Fgeodynamics-course%252Ftutorials%252Fintro.ipynb
```

### Generate URLs with the Binder Wizard

The Underworld3 repository includes a script to generate launch URLs and badges:

```bash
# Interactive wizard
python scripts/binder_wizard.py

# Quick generation (outputs a markdown badge)
python scripts/binder_wizard.py myuser/geodynamics-course main tutorials/intro.ipynb
```

The wizard generates ready-to-paste badges in Markdown, HTML, and reStructuredText formats.

See: [scripts/binder_wizard.py](https://github.com/underworldcode/underworld3/blob/development/scripts/binder_wizard.py)

### Adding a Badge to Your Repository

Copy one of these templates into your README, replacing the placeholders:

**Markdown:**
```markdown
[![Launch in Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development?urlpath=git-pull%3Frepo%3Dhttps%253A%252F%252Fgithub.com%252FYOUR_USER%252FYOUR_REPO%26branch%3Dmain%26urlpath%3Dlab%252Ftree%252FYOUR_REPO)
```

**HTML:**
```html
<a href="https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development?urlpath=git-pull%3Frepo%3Dhttps%253A%252F%252Fgithub.com%252FYOUR_USER%252FYOUR_REPO%26branch%3Dmain%26urlpath%3Dlab%252Ftree%252FYOUR_REPO">
  <img src="https://mybinder.org/badge_logo.svg" alt="Launch in Binder">
</a>
```

### What Happens When Users Click the Badge

1. mybinder.org launches the pre-built Underworld3 environment (cached, fast)
2. nbgitpuller clones your repository into the JupyterLab workspace
3. JupyterLab opens at the specified notebook or directory
4. Your repository is pulled fresh on each launch (updates are automatic)

### Requirements for Your Repository

- Must be **public** on GitHub
- Notebooks should use the `python3` kernel
- No `.binder/` directory or Dockerfile needed
- Import Underworld3 as: `import underworld3 as uw`

## How It Works

This minimal repository provides a stable [mybinder.org](https://mybinder.org) cache. The actual Underworld3 code is pulled fresh from the pre-built base image on each launch.

```
mybinder.org
    |
    +-- Pulls pre-built image from GHCR
    |   ghcr.io/underworldcode/uw3-base:<branch>-slim
    |
    +-- Caches by this repo's commit hash
        (rarely changes -> fast launches)

On container start:
    |
    +-- Pulls latest underworld3 code (branch set by UW3_BRANCH)
    +-- Quick rebuild (~30 seconds)
    +-- Launches JupyterLab
```

## Maintenance

This repo only needs updating when:
- The base image version changes (update `FROM` tag in `.binder/Dockerfile`)
- A new underworld3 branch needs a launcher (create a new branch here)

Code changes to Underworld3 are pulled automatically on each launch. Image updates are automated via GitHub Actions `repository_dispatch`.

### Adding a New Branch

1. Create a new branch: `git checkout -b <branch-name>`
2. Edit `.binder/Dockerfile` to set `ENV UW3_BRANCH=<underworld3-branch>`
3. Push: `git push origin <branch-name>`

## Links

- **Underworld3 repository**: https://github.com/underworldcode/underworld3
- **Documentation**: https://underworldcode.github.io/underworld3/
- **Base image**: https://github.com/underworldcode/underworld3/pkgs/container/uw3-base
- **Container documentation**: https://github.com/underworldcode/underworld3/blob/development/docs/developer/subsystems/containers.md

## Superseded Repositories

The following older launcher repositories in `underworld-community` are **superseded** by this repository:

- `underworld-community/uw-demo-launcher` - Combined UW2+UW3 demo (now outdated)
- `underworld-community/uw3-demo-launcher-dev` - UW3-only dev demo (now outdated)

These used a different architecture (conda environment + source build) and do not benefit from the pre-built image caching or automated updates provided here.
