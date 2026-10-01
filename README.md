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
| 0.8.0 (latest in this repository) | v0.12.0 and v0.11.108; the v0.12 commands (`dk capabilities`, `dk attachment`, `--lang`, ...) need v0.12.0, see the [dk 0.8.0 release](https://github.com/dakera-ai/dakera-cli/releases/tag/v0.8.0) |
| 0.7.x | v0.11.108 |

## Updates

Packages are published automatically by the `Publish Linux Packages` workflow of [dakera-cli](https://github.com/dakera-ai/dakera-cli) when a release tag is pushed: it builds the package, adds it to this repository, regenerates and signs the repository metadata and commits. Nothing here is edited by hand. The repository metadata is signed (`repodata/repomd.xml.asc`, the same key as the [APT repository](https://dakera-ai.github.io/apt-repo/KEY.gpg)); the packages themselves are not, which is why `dakera.repo` sets `gpgcheck=0`.
