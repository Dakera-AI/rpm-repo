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

| Package | Description |
|---------|-------------|
| `dk` | Dakera CLI — manage AI agent memory from the command line |

## Updates

Packages are automatically published when a new version of dakera-cli is released.
