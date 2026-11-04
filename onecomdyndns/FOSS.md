# foss Notice

This project and distribution include the following notable Open Source
components and their licenses. See `sbom.md` and `sbom.json` for the full
machine-readable Software Bill of Materials.

Release: 1.5.8 (2026-11-04)

Core components:

- `requests >=2.34.2` — Apache-2.0
- `acme >=5.9.0` — Apache-2.0
- `josepy >=2.2.0` — Apache-2.0
- `cryptography >=50.0.2` — Apache-2.0 / BSD-3-Clause
- Home Assistant Base Python / Supervisor API — Apache-2.0
- Python 3 from the Home Assistant base image — PSF-2.0
- Alpine Linux 3.24, musl and libffi — various / MIT

Development & testing:

- `pytest >=9.2.0` — MIT
- `pytest-asyncio >=1.4.1.post1` — Apache-2.0
- `pytest-cov >=7.1.0` — MIT
- `responses >=0.26.3` — Apache-2.0
- `ruff >=0.17.3` — MIT
- `bandit 1.9.4` — Apache-2.0
- `pip-audit 2.10.1` — Apache-2.0
- `safety 3.8.1` — MIT

The declared runtime dependency versions are also recorded in `sbom.json`.
`pip_audit.json` is a scan report for the environment used to generate it and
may not reflect the latest compatible versions in `requirements.txt`.

License for this project: MIT

If you need a formal third-party license report (for compliance), please open an
issue and I will generate a SPDX-compatible license manifest from the sbom.
