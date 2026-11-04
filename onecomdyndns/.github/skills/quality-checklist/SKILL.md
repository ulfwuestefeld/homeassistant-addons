---
name: quality-checklist
description: One.com DynDNS Updater release and version checklist. Use before a release; for routine post-change validation use the repository-wide quality-gate skill.
---

# One.com Release Checklist

For post-change validation after meaningful changes, use the repository-wide [quality gate](../../../../.github/skills/quality-gate/SKILL.md). This skill covers One.com-specific release and version checks.

Before releasing, verify:

- [ ] CHANGELOG.md has the release entry and user-facing documentation is current
- [ ] Version in config.yaml, manifest.json, sbom.json, and sbom.md matches CHANGELOG
- [ ] Test documentation (Test.md) is current when Python support or test count changes
- [ ] Relevant tests pass, including the project test suite
- [ ] sbom.json and sbom.md reflect dependency versions and release date
- [ ] .gitignore covers IDE and build artifacts

## Version Bump Process

When releasing a new version, update **all** of these files:

1. `config.yaml` → `version: "X.Y.Z"`
2. `custom_components/onecom_dyndns/manifest.json` → `"version": "X.Y.Z"`
3. `sbom.json` → `"version": "X.Y.Z"` and `"serialNumber": "...vX.Y.Z"`
4. `sbom.md` → Version string, table row, dependency graph
5. `CHANGELOG.md` → New `## [X.Y.Z] - YYYY-MM-DD` section; update "Custom component" range
6. `Test.md` → Python version requirement if changed, test count if changed

Verify version references with `rg "old.version"` to find any missed occurrences.

## Resources

- Home Assistant Developer Docs: https://developers.home-assistant.io/
- Let's Encrypt: https://letsencrypt.org/docs/
- GitHub: https://github.com/ulfwuestefeld/homeassistant-onecom-dyndns