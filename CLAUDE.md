# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

## Project Overview

This repository maintains a canonical pre-commit configuration template that gets copied to other new repos. It serves as a single source of truth for pre-commit hook configurations.

## Key Files

- `.pre-commit-config.yaml` - Main pre-commit hooks configuration
- `pyproject.toml` - Ruff linter configuration with lint rule selections

## Pre-commit Hooks

The configuration includes these hook repositories:

1. **pre-commit-hooks** - Standard checks (large files, case conflicts, JSON/TOML/YAML validation, private key detection)
2. **ruff-pre-commit** - Python linting and formatting (excludes notebooks due to magic cell issues)
3. **nbQA** - Runs ruff on Jupyter notebooks with specific ignore rules for Databricks compatibility (F821 for dbutils/spark)
4. **mypy** - Static type checking
5. **nbstripout** - Strips output from Jupyter notebooks

## Common Commands

```bash
# Run hooks on all files without committing
pre-commit run --all-files

# Update hook versions
pre-commit autoupdate
```

## Ruff Configuration

The `pyproject.toml` configures ruff to check: pycodestyle (E), Pyflakes (F), pyupgrade (UP), flake8-bandit (S), flake8-bugbear (B), flake8-simplify (SIM), isort (I), and pylint (PL).

## CI Integration

Pre-commit CI is configured to autoupdate quarterly.
