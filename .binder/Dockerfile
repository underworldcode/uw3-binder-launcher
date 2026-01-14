# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Start script does fast git pull (shallow clone) then launches Jupyter
#
# Requires container sha256:dc1f6bcd18d19b87c227503c415fd180471576a89c5334d55ad72565665b6d3c

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Branch to pull at startup (shallow git pull)
ENV UW3_BRANCH=uw3-release-candidate
