# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image includes JIT compiler toolchain (with libexec/cc1) and Mesa software rendering
# Split layers for reliable binder uploads
#
# Requires container sha256:9bd06ad9176e64496df498829f6fbfcb9dc50eac91e0f53a317f9a4edef70308

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Code is frozen at image build time (from uw3-release-candidate branch)
ENV UW3_BRANCH=uw3-release-candidate
