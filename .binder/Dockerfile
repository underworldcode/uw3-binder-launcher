# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image includes JIT compiler toolchain and Mesa software rendering
# Split layers for reliable binder uploads
#
# Requires container sha256:361fe787af610d07544d798235991af51a25a36fafe0a538027223c7816da07c

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Code is frozen at image build time (from uw3-release-candidate branch)
ENV UW3_BRANCH=uw3-release-candidate
