---
name: homeassistant-addons
description: "Repository-wide guidance for the two Home Assistant add-on projects in this repository. Use when a request spans both projects, the target project is unclear, or shared repository files are involved."
---

# Home Assistant Add-ons

This repository contains two independent projects: One.com DynDNS Updater and Gas & Water Meter. Use this skill to choose the right project and shared workflow; use the linked project skills for implementation details.

## Choose the project

| Project | Directory | Use its skills when working on |
|---|---|---|
| One.com DynDNS Updater | `onecomdyndns/` | DNS updates, ACME/SSL, its Home Assistant integration, or its tests |
| Gas & Water Meter | `gasandwater/` | Meter readings, calculations, SQLite/legacy storage, OCR, APIs, frontend, or its tests |

If a request concerns a single add-on, keep changes within that project. Only change root-level repository files when the request actually affects both projects or repository-wide documentation/metadata.

## Shared working rules

- Treat each project as independent: do not share dependencies, environments, configuration, or project-specific assumptions.
- Before editing, identify the affected project and consult the relevant project skill below. The projects use different Home Assistant patterns, async test setups, and quality checks; do not transfer a convention from one project to the other without verifying it.
- Follow the target project's existing structure and update its directly related tests, translations, documentation, and release metadata when applicable.
- Always write `sbom` and `foss` in lowercase, including filenames, prose, and documentation (for example `sbom.json`, `sbom.md`, and `foss.md`).
- Run validation from the target project directory. For Gas & Water Meter frontend changes, use its separate `frontend-src` toolchain.
- For setup instructions and the repository's canonical test commands, see the [repository README](../../../README.md).
- After meaningful changes, apply the repository-wide [quality gate](../quality-gate/SKILL.md) along with the target project's checks.

## Project skills

### One.com DynDNS Updater

- [Project architecture and deployment](../../../onecomdyndns/.github/skills/project-overview/SKILL.md)
- [Python standards](../../../onecomdyndns/.github/skills/python-standards/SKILL.md)
- [Home Assistant integration conventions](../../../onecomdyndns/.github/skills/ha-integration/SKILL.md)
- [Testing conventions](../../../onecomdyndns/.github/skills/testing/SKILL.md)
- [ACME and SSL conventions](../../../onecomdyndns/.github/skills/acme-ssl/SKILL.md)
- [Security conventions](../../../onecomdyndns/.github/skills/security/SKILL.md)
- [File structure](../../../onecomdyndns/.github/skills/file-structure/SKILL.md)
- [Quality and release checklist](../../../onecomdyndns/.github/skills/quality-checklist/SKILL.md)

### Gas & Water Meter

- [Gas & Water Meter project skill](../../../gasandwater/.github/skills/gas-water-meter-project/SKILL.md) — architecture, implementation patterns, tests, and release guidance.
