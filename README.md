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

Packages are published automatically by the `Publish Linux Packages` workflow of [dakera-cli](https://github.com/dakera-ai/dakera-cli) when a release tag is pushed: it builds the package, adds it to this repository, regenerates and signs the repository metadata and commits. Nothing here is edited by hand. Every package and the repository metadata (`repodata/repomd.xml.asc`) are signed with the same key as the [APT repository](https://dakera-ai.github.io/apt-repo/KEY.gpg); the public key is published here as `RPM-GPG-KEY-dakera`.

## Verifying signatures

`dakera.repo` enables `gpgcheck=1` (package signatures) and `repo_gpgcheck=1` (metadata signature) and points `gpgkey` at `RPM-GPG-KEY-dakera`, so `dnf` and `yum` verify both. On first install they ask you to confirm the key.

To verify a downloaded package by hand:

```bash
curl -fsSLO https://dakera-ai.github.io/rpm-repo/RPM-GPG-KEY-dakera
sudo rpm --import RPM-GPG-KEY-dakera
curl -fsSLO https://dakera-ai.github.io/rpm-repo/packages/dk-0.8.0-1.x86_64.rpm
rpm -K dk-0.8.0-1.x86_64.rpm   # expect: digests signatures OK
```

If you added the repository before packages were signed, refresh your copy of the repo file to turn verification on:

```bash
sudo curl -fsSL -o /etc/yum.repos.d/dakera.repo https://dakera-ai.github.io/rpm-repo/dakera.repo
```
