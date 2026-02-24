# Binder launcher for Underworld3 - main branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# The start script pulls the underworld3 branch specified by UW3_BRANCH.
#
# Direct launch:
#   https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main
#
# Launch with your repository (via nbgitpuller):
#   https://mybinder.org/v2/gh/underworldcode/uw3-binder-launcher/main
#     ?urlpath=git-pull?repo=<your-repo-url>&branch=<branch>&urlpath=lab/tree/<repo-name>
#
# See: https://github.com/underworldcode/underworld3/blob/main/scripts/binder_wizard.py

FROM ghcr.io/underworldcode/uw3-base:-slim

# Pull from main branch of underworld3
ENV UW3_BRANCH=main
