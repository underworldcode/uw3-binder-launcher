# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image includes JIT compiler toolchain (with libexec/cc1) and Mesa software rendering
# Split layers for reliable binder uploads
# Includes jupyter-server-proxy for trame PyVista backend
#
# Requires container sha256:f3523b871c9d19a2d5a6d44baaa652a82a7a2f9c14f70eddebd3b2361ff11e25

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Code is frozen at image build time (from uw3-release-candidate branch)
ENV UW3_BRANCH=uw3-release-candidate
