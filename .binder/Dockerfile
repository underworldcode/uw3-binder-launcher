# Generic Binder Launcher for Underworld3
# ========================================
#
# This launcher provides the Underworld3 environment for ANY repository.
#
# Features:
# - Pre-built UW3 environment (cached for fast launches)
# - nbgitpuller for cloning any content repository
# - JIT compiler toolchain for custom extensions
# - Mesa software rendering for visualization
# - Split layers for reliable mybinder.org uploads
#
# Usage:
# 1. Direct launch (UW3 tutorials):
#    https://mybinder.org/v2/gh/underworldcode/uw3-launcher/main
#
# 2. Launch with your repository (via nbgitpuller):
#    https://mybinder.org/v2/gh/underworldcode/uw3-launcher/main
#      ?urlpath=git-pull?repo=<your-repo-url>&branch=<branch>&urlpath=lab/tree/<repo-name>
#
# See: https://github.com/underworldcode/underworld3/blob/main/scripts/binder_wizard.py
#      for generating launch URLs
#
# Image SHA: sha256:692228fca8e37e2d18209199ba74329ca6dfb7133be2dda0cab3879144707d73

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Default branch for UW3 content (used when launching tutorials directly)
ENV UW3_BRANCH=uw3-release-candidate
