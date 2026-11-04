# sbom (Software Bill of Materials)

## Gas & Water Meter Add-on v0.4.4

### Metadata

- **Name**: Gas & Water Meter
- **Domain**: gas_water_meter
- **Version**: 0.4.4
- **Frontend panel package**: 0.1.9
- **Type**: Home Assistant Add-on + Custom Integration
- **Python**: >= 3.12
- **Home Assistant**: >= 2024.1.0

### Add-on Container Components

| Package | Type | License |
|---------|------|---------|
| Home Assistant base image (`amd64-base` / `aarch64-base`) | Container image (2026.10.3) | Multiple; see image inventory |
| Alpine Linux | Operating system (3.24) | MIT |
| tesseract-ocr | System binary (pre-installed) | Apache-2.0 |
| bashio | Shell library | Apache-2.0 |

### Direct Python Dependencies

| Package | Version Constraint | Type | License |
|---------|--------------------|------|---------|
| pytesseract | >= 0.3.13 | Runtime (optional) | Apache-2.0 |
| aiosqlite | >= 0.22.1 | Runtime (required) | MIT |
| pillow-heif | >= 0.22.0 | Runtime (required) | BSD-3-Clause |
| tesseract-ocr | >= 4.0 | System binary (optional) | Apache-2.0 |
| libheif | (system) | System library (required) | LGPL-3.0 |

### Direct Frontend Dependencies

| Package | Version Constraint | Type | License |
|---------|--------------------|------|---------|
| lit | ^3.3.3 | Runtime (bundled) | BSD-3-Clause |
| chart.js | ^4.6.1 | Runtime (bundled) | MIT |

### Frontend Build & Test Dependencies

| Package | Version Constraint | Type | License |
|---------|--------------------|------|---------|
| rollup | ^4.67.5 | Build tool | MIT |
| @rollup/plugin-node-resolve | ^16.0.3 | Build tool | MIT |
| @rollup/plugin-terser | ^1.0.2 | Build tool | MIT |
| @web/test-runner | ^1.0.0 | Test runner | MIT |
| @web/test-runner-commands | ^1.0.1 | Test helper | MIT |
| @open-wc/testing | ^5.0.0 | Test utility | MIT |

### Security Hardening Overrides

| Package | Version Constraint | Purpose |
|---------|--------------------|---------|
| koa | ^2.16.4 | Pinned to patched middleware version |
| nanoid | ^3.3.20 | Pinned to patched ID generator |
| picomatch | ^4.0.7 | Pinned to patched glob matching version |
| qs | ^6.17.1 | Pinned to patched query-string parser |
| ws | ^8.22.1 | Pinned to patched websocket implementation |

### HA Core Built-in Dependencies Used

| Package | Usage |
|---------|-------|
| voluptuous | Config flow & service schema validation |
| Pillow | Image preprocessing for OCR, EXIF extraction |
| aiohttp | REST API for image uploads |
| homeassistant.helpers.update_coordinator | Data coordination |

### Test Dependencies

| Package | Version Constraint | License |
|---------|--------------------|---------|
| pytest | Python-specific versions; see `requirements_test.txt` | MIT |
| pytest-asyncio | Python-specific versions; see `requirements_test.txt` | Apache-2.0 |
| pytest-homeassistant-custom-component | 0.13.205 (Python 3.12), 0.13.316 (3.13), 0.13.375 (3.14) | MIT |
| pytest-cov | Python-specific versions; see `requirements_test.txt` | MIT |
| pytest-timeout | Python-specific versions; see `requirements_test.txt` | MIT |
| ruff | >= 0.17.3 | MIT |

The Home Assistant test package pins its test stack and Pillow version. The
Python 3.12–3.14 markers in `requirements_test.txt` keep each CI job on the
newest compatible set. `pillow-heif>=0.22.0` permits the newest release whose
Pillow requirement is compatible with each supported Home Assistant release.

### Transitive Dependencies

pytesseract depends on:
- Pillow (already in HA core)

pillow-heif depends on:
- libheif (system library, dynamically linked via LGPL-3.0)
- Pillow (already in HA core)

lit depends on:
- @lit/reactive-element, lit-element, lit-html (all BSD-3-Clause, bundled)

No additional transitive runtime dependencies beyond those bundled are introduced.
