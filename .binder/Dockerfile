# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image uses split layers (<500MB each) for reliable binder uploads
# Start script does fast git pull (shallow clone) then launches Jupyter
#
# Requires container sha256:793fe8c557ce1675d11d044baca75fbf4e8935c4f459af71d7151be09516cefc

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Branch to pull at startup (shallow git pull)
ENV UW3_BRANCH=uw3-release-candidate
