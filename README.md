# OPAL Developer Images

This repository is not the core OPAL codebase. It defines a modular collection of container images and devcontainer wiring used to run and develop OPAL in a clean, reproducible environment.

The goal is simple:

- centralize runtime and tooling dependencies,
- publish/update images independently (via GHCR),
- keep local developer setup lightweight.

## What this repository contains

- `.devcontainer/docker-compose.yml`: service composition for the local development environment.
- `.devcontainer/.env`: image references for each service (for example, `ghcr.io/...:latest`).
- `.devcontainer/devcontainer.json`: VS Code devcontainer integration.

## How it works

The compose file uses environment variables for images (for example `OPAL_ANALYSIS_IMAGE`, `OPAL_VKG_IMAGE`, `OPAL_FRONTEND_IMAGE`, `OPAL_REASONER_IMAGE`).

This lets you:

- swap image tags without editing compose structure,
- keep the setup modular across services,
- update dependencies by publishing new image versions.

## Typical workflow

1. Update image tags in `.devcontainer/.env`.
2. Rebuild/reopen the devcontainer in VS Code.
3. Start working with all OPAL dependencies pre-integrated.

## Scope

This repo is focused on environment definition and dependency integration. Application logic and OPAL library development live in their respective project repositories.