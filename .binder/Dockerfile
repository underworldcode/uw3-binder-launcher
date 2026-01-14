# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# The start script pulls the underworld3 branch specified by UW3_BRANCH.
#
# Requires container sha256:f3f865b1cd23b65c343fd5c536e0521fdc79d771d3ea0d5bc907d9c509439624

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Pull from uw3-release-candidate branch of underworld3
ENV UW3_BRANCH=uw3-release-candidate
