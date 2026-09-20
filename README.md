# WizkBuilder

WizkBuilder is a multi-stage Docker build that packages a reusable GitHub Actions-friendly development environment for building, testing, and shipping projects across multiple languages and toolchains.

The image is published to GitHub Container Registry (GHCR) as:

- `ghcr.io/wizk-modz/builder:base`
- `ghcr.io/wizk-modz/builder:cpp-py`
- `ghcr.io/wizk-modz/builder:full`
- `ghcr.io/wizk-modz/builder:latest`

## Why this project exists

This repository provides a consistent containerized environment for CI and local development. Instead of installing toolchains ad hoc, you can use a prebuilt image with a curated stack for common build workflows.

## Included targets

### base
The minimal base image includes:

- Ubuntu 26.04
- UTF-8 locale configuration
- a non-root `builder` user
- `sudo` access for the builder user
- standard GitHub Actions-friendly tooling such as `git`, `curl`, `wget`, `tar`, and `ca-certificates`

### cpp-py
Adds the core toolchain for native and Python development:

- GCC/Clang toolchain
- CMake, Ninja, Meson, Autotools
- Python 3 + pip + venv
- `ccache`
- `jq`, `rsync`, `zip`, `unzip`, `gnupg`, `ssh`

### full
Extends the C/C++ + Python image with additional ecosystems used in modern software projects:

- Node.js LTS
- Yarn
- Go
- Rust
- Java 21 + Maven + Gradle
- Docker CLI + Buildx plugin
- GitHub CLI (`gh`)

## Quick start

Pull the image:

```bash
docker pull ghcr.io/wizk-modz/builder:full
