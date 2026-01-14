# Binder launcher for Underworld3 - uw3-release-candidate branch
# Uses pre-built base image from GHCR
#
# This repo exists separately so mybinder.org can cache the image.
# Image uses split layers (<500MB each) for reliable binder uploads
# Minimal start script - just sets PATH and launches jupyter directly
#
# Requires container sha256:9570cd868e224fdae01d83a9e3960ef656db791e9ef7361ae6cf384875be55f5

FROM ghcr.io/underworldcode/uw3-base:2025.01-slim

# Code is frozen at image build time (from uw3-release-candidate branch)
ENV UW3_BRANCH=uw3-release-candidate
