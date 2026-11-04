# sbom (Software Bill of Materials)

**Project:** One.com DynDNS Updater  
**Version:** 1.5.8<br>
**Date:** 2026-11-04<br>
**License:** MIT  

## Overview

This document provides a complete inventory of all software components used in the One.com DynDNS Updater Home Assistant add-on.

## Application Components

| Component | Version | License | Description |
|-----------|---------|---------|-------------|
| One.com DynDNS Updater | 1.5.8 | MIT | Main application |

### Source Files

| File | Purpose |
|------|---------|
| `run.py` | Main entry point, orchestrates DynDNS and SSL management |
| `onecom_api.py` | One.com API client for DNS management |
| `acme_manager.py` | ACME/Let's Encrypt protocol implementation |
| `certificate_manager.py` | SSL certificate lifecycle management |

## Runtime Dependencies

### Python Packages (Production -- Add-on)

| Package | Min. Version | License | Purpose |
|---------|--------------|---------|---------|
| requests | 2.34.2 | Apache-2.0 | HTTP client for API calls |
| acme | 5.9.0 | Apache-2.0 | Let's Encrypt ACME protocol |
| josepy | 2.2.0 | Apache-2.0 | JOSE/JWK cryptographic operations |
| cryptography | 50.0.2 | Apache-2.0 / BSD-3-Clause | Cryptographic primitives |

### Python Packages (Production -- Custom Integration)

| Package | Version | License | Purpose |
|---------|---------|---------|---------|
| acme | 5.9.0 | Apache-2.0 | Let's Encrypt ACME protocol |
| josepy | 2.2.0 | Apache-2.0 | JOSE/JWK cryptographic operations |

> `requests` and `cryptography` are provided by Home Assistant Core but the add-on pins/declares compatible versions for the bundled environment.

### Python Packages (Development/Testing)

| Package | Min. Version | License | Purpose |
|---------|--------------|---------|---------|
| pytest | >=9.2.0 | MIT | Testing framework |
| pytest-cov | >=7.1.0 | MIT | Code coverage |
| pytest-asyncio | >=1.4.1.post1 | Apache-2.0 | Async test support |
| responses | >=0.26.3 | Apache-2.0 | HTTP mocking |
| pytest-homeassistant-custom-component | 0.13.375 (Python 3.14) | MIT | HA integration test framework (optional) |
| ruff | >=0.17.3 | MIT | Linting |
| bandit | 1.9.4 | Apache-2.0 | Security analysis |
| pip-audit | 2.10.1 | Apache-2.0 | Dependency vulnerability audit |
| safety | 3.8.1 | MIT | Dependency vulnerability audit |

## Container Base Image

| Component | Version | License | Registry |
|-----------|---------|---------|----------|
| Home Assistant Base (`amd64-base` / `aarch64-base`) | 2026.10.3 (Alpine 3.24) | Multiple; see image inventory | ghcr.io/home-assistant |

### Supported Architectures

- `amd64` (x86_64)
- `aarch64` (ARM64)

## Operating System Components (Alpine Linux 3.24)

| Package | License | Purpose |
|---------|---------|---------|
| python3 | PSF-2.0 | Python 3 runtime from Alpine |
| py3-pip | MIT | Python package manager |
| py3-requests | Apache-2.0 | Pre-built requests package |
| py3-cryptography | Apache-2.0 / BSD | Pre-built cryptography package |
| py3-openssl | Apache-2.0 | OpenSSL Python bindings |
| openssl | Apache-2.0 | SSL/TLS library |
| libffi | MIT | Foreign function interface |
| gcc | GPL-3.0 | C compiler (build-time) |
| musl | MIT | C standard library |

## External Services

| Service | Purpose | URL |
|---------|---------|-----|
| One.com | DNS management | https://www.one.com |
| Let's Encrypt | SSL certificate issuance | https://letsencrypt.org |
| ipify | Public IP detection | https://api.ipify.org |
| ifconfig.me | Public IP detection (fallback) | https://ifconfig.me |
| icanhazip.com | Public IP detection (fallback) | https://icanhazip.com |
| Google DNS | DNS propagation verification | https://dns.google |

## License Summary

| License | Components |
|---------|------------|
| MIT | Main application, libffi, musl, pytest, pytest-cov |
| Apache-2.0 | requests, acme, josepy, openssl, Home Assistant base |
| BSD-3-Clause | cryptography (dual-licensed) |
| PSF-2.0 | Python |
| GPL-3.0 | gcc (build-time only) |

## Security Considerations

- All dependencies are from trusted sources (PyPI, Alpine packages, Home Assistant registry)
- Review the current `pip_audit.json` and container scan for release-time
  vulnerability status; dependency versions and advisories change over time.
- Credentials are stored in Home Assistant add-on configuration (encrypted)
- HTTPS used for all external communications

## Dependency Graph

```
One.com DynDNS Updater (1.5.8)
├── Python 3 (Alpine package)
│   └── Alpine Linux 3.24
│       ├── openssl
│       ├── libffi
│       └── musl
├── requests (>=2.34.2)
│   ├── urllib3
│   ├── certifi
│   └── charset-normalizer
├── acme (>=5.9.0)
│   ├── josepy (>=2.2.0)
│   ├── cryptography (>=50.0.2)
│   │   └── cffi
│   └── requests
└── Home Assistant Supervisor API
```

## sbom Format

This sbom is also available in machine-readable CycloneDX JSON format: `sbom.json`

## Contact

For security issues or dependency updates, please open an issue at:
https://github.com/ulfwuestefeld/homeassistant-onecom-dyndns/issues
