# Binder launcher for Underworld3 - development branch
# =====================================================
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
#    https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development
#
# 2. Launch with your repository (via nbgitpuller):
#    https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/development
#      ?urlpath=git-pull?repo=<your-repo-url>&branch=<branch>&urlpath=lab/tree/<repo-name>
#
# See: https://github.com/underworldcode/underworld3/blob/main/scripts/binder_wizard.py
#      for generating launch URLs

FROM ghcr.io/underworldcode/uw3-base:development-slim

# Pull from development branch of underworld3
ENV UW3_BRANCH=development
