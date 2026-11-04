# foss (Free and Open Source Software) Dependencies

This document lists all third-party open source components used by the Gas & Water Meter add-on and integration.

## Project Version

0.4.4

## Runtime Dependencies (Python)

| Component | Version | License | URL |
|-----------|---------|---------|-----|
| pytesseract | >= 0.3.13 | Apache-2.0 | https://github.com/madmaze/pytesseract |
| aiosqlite | >= 0.22.1 | MIT | https://github.com/omnilib/aiosqlite |
| pillow-heif | >= 0.22.0 | BSD-3-Clause | https://github.com/bigcat88/pillow_heif |
| tesseract-ocr (system) | >= 4.0 | Apache-2.0 | https://github.com/tesseract-ocr/tesseract |

## Runtime Dependencies (Frontend, bundled)

| Component | Version | License | URL |
|-----------|---------|---------|-----|
| lit | ^3.3.3 | BSD-3-Clause | https://github.com/lit/lit |
| chart.js | ^4.6.1 | MIT | https://github.com/chartjs/Chart.js |

## Frontend Build & Test Dependencies

| Component | Version | License | URL |
|-----------|---------|---------|-----|
| rollup | ^4.67.5 | MIT | https://github.com/rollup/rollup |
| @rollup/plugin-node-resolve | ^16.0.3 | MIT | https://github.com/rollup/plugins |
| @rollup/plugin-terser | ^1.0.2 | MIT | https://github.com/rollup/plugins |
| @web/test-runner | ^1.0.0 | MIT | https://github.com/modernweb-dev/web |
| @web/test-runner-commands | ^1.0.1 | MIT | https://github.com/modernweb-dev/web |
| @open-wc/testing | ^5.0.0 | MIT | https://github.com/open-wc/open-wc |

### Security override pins

These transitive packages were explicitly pinned to patched versions to remove known advisories from the installed npm graph:

| Package | Version | Reason |
|---------|---------|--------|
| koa | ^2.16.4 | Mitigates known request smuggling / middleware vulnerabilities |
| nanoid | ^3.3.20 | Mitigates predictable ID generation issues |
| picomatch | ^4.0.7 | Mitigates ReDoS / path traversal exposure in vulnerable versions |
| qs | ^6.17.1 | Mitigates prototype pollution and parsing issues |
| ws | ^8.22.1 | Mitigates DoS / parser issues in old websocket versions |

## Add-on Container Dependencies

| Component | License | Usage |
|-----------|---------|-------|
| Alpine Linux | MIT | Add-on base image (via HA base image) |
| libheif | LGPL-3.0 | HEIC/HEIF image decoding (system library, dynamically linked) |
| bashio | Apache-2.0 | Add-on shell scripting helper |

## Home Assistant Core Dependencies (always available)

| Component | License | Usage |
|-----------|---------|-------|
| voluptuous | BSD-3-Clause | Schema validation in config flow and services |
| Pillow | HPND | Image preprocessing for OCR, EXIF extraction |
| aiohttp | Apache-2.0 | REST API for image uploads (via HA core) |

## Test Dependencies (Python)

| Component | Version | License | URL |
|-----------|---------|---------|-----|
| pytest | Python-specific versions; see `requirements_test.txt` | MIT | https://github.com/pytest-dev/pytest |
| pytest-asyncio | Python-specific versions; see `requirements_test.txt` | Apache-2.0 | https://github.com/pytest-dev/pytest-asyncio |
| pytest-homeassistant-custom-component | 0.13.205 (Python 3.12), 0.13.316 (3.13), 0.13.375 (3.14) | MIT | https://github.com/MatthewFlamworthy/pytest-homeassistant-custom-component |
| pytest-cov | Python-specific versions; see `requirements_test.txt` | MIT | https://github.com/pytest-dev/pytest-cov |
| pytest-timeout | Python-specific versions; see `requirements_test.txt` | MIT | https://github.com/pytest-dev/pytest-timeout |
| ruff | >= 0.17.3 | MIT | https://github.com/astral-sh/ruff |

## Test Dependencies (Frontend)

| Component | Version | License | URL |
|-----------|---------|---------|-----|
| @web/test-runner | ^0.20.2 | MIT | https://github.com/modernweb-dev/web |
| @open-wc/testing | ^5.0.0 | MIT | https://github.com/open-wc/open-wc |
| @web/test-runner-commands | ^1.0.1 | MIT | https://github.com/modernweb-dev/web |

## License Compatibility

All listed dependencies use licenses compatible with the MIT license of this project:
- MIT: Same license
- Apache-2.0: Compatible with MIT
- BSD-3-Clause: Compatible with MIT
- LGPL-3.0: Compatible with MIT (dynamically linked)
- HPND (Historical Permission Notice and Disclaimer): Compatible with MIT
