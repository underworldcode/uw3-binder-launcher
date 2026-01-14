# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image includes JIT compiler toolchain (with libexec/cc1) and Mesa software rendering
# Split layers for reliable binder uploads
# Includes jupyter-server-proxy for trame PyVista backend
#
# Requires container sha256:6d3894260f28dc837a21ce77a94bb1781f4ca12422934be7a4bd34b4a7b1223f

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Code is frozen at image build time (from uw3-release-candidate branch)
ENV UW3_BRANCH=uw3-release-candidate
