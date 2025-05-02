# DNS Management for srajasimman.dev

[![octodns-sync](https://github.com/srajasimman/dns/actions/workflows/octodns-sync.yaml/badge.svg)](https://github.com/srajasimman/dns/actions/workflows/octodns-sync.yaml)

This repository manages DNS configuration for `srajasimman.dev` using [OctoDNS](https://github.com/github/octodns), which allows for version-controlled DNS management through YAML files.

## Overview

The DNS records are configured in YAML files and automatically synced to Cloudflare using GitHub Actions. This approach provides:
- Version control for all DNS changes
- Peer review through pull requests
- Automatic validation and deployment
- Centralized management for multiple domains

## Repository Structure

```
├── .github/workflows/   # GitHub Actions workflow definitions
├── bin/                 # Helper scripts
│   ├── dry-run          # Test DNS changes without applying
│   └── sync             # Apply DNS changes to providers
├── config/              # OctoDNS configuration
│   └── production.yaml  # Main configuration file
└── *.yaml               # Domain-specific DNS records (e.g., srajasimman.dev.yaml)
```

## How It Works

1. DNS records are defined in YAML files (e.g., `srajasimman.dev.yaml`)
2. GitHub Actions workflow validates and applies changes:
   - Pull requests: Dry run only (validation)
   - Pushes to main: Apply changes to DNS providers

## Making Changes

1. Create a branch for your changes
2. Edit the appropriate YAML file to add, modify, or remove DNS records
3. Submit a pull request
4. GitHub Actions will validate your changes
5. Once approved and merged, changes will be automatically deployed

## Local Testing

Before submitting a pull request, you can test your changes locally:

```bash
# Install dependencies
pip install -r requirements.txt

# Run a dry-run to validate changes
./bin/dry-run

# If you have proper credentials configured, you can sync changes
# (Use with caution!)
./bin/sync
```

## Required Environment Variables

The following secrets are required for deployment:
- `CLOUDFLARE_TOKEN`: API token for Cloudflare access
- `CLOUDFLARE_ACCOUNT_ID`: Cloudflare account identifier

These are configured as GitHub repository secrets for the GitHub Actions workflow.

## Further Information

For more details about OctoDNS configuration and usage, please refer to the [OctoDNS documentation](https://github.com/github/octodns).

