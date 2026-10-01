# Dakera RPM Repository

DNF/YUM package repository for [Dakera AI](https://dakera.ai) tools.

## Install

```bash
# Add Dakera repository
sudo dnf config-manager --add-repo https://dakera-ai.github.io/rpm-repo/dakera.repo

# Install dk CLI
sudo dnf install dk
```

## Packages

| Package | Description | Architecture |
|---------|-------------|--------------|
| `dk` | Dakera CLI: manage AI agent memory from the command line | x86_64 only |

Only the `dk` CLI is packaged here. The Dakera server is not: it ships as the container image `ghcr.io/dakera-ai/dakera` (see [dakera-deploy](https://github.com/dakera-ai/dakera-deploy)). `dakera-mcp` is distributed through the [Homebrew tap](https://github.com/dakera-ai/homebrew-tap) and its own releases.

## Server compatibility

| `dk` version | Dakera server |
|--------------|---------------|
| 0.7.x (latest in this repository) | v0.11.108 |
| 0.8.0 and later | v0.11.108 and v0.12.0, with the v0.12 commands (`dk capabilities`, `dk attachment`, ...), see [dakera-cli#152](https://github.com/dakera-ai/dakera-cli/pull/152) |

## Updates

Packages are published automatically by the `Publish Linux Packages` workflow of [dakera-cli](https://github.com/dakera-ai/dakera-cli) when a release tag is pushed: it builds the package, adds it to this repository, regenerates and signs the repository metadata and commits. Nothing here is edited by hand, so `dk` 0.8.0 appears in this repository after the dakera-cli release, not before.
