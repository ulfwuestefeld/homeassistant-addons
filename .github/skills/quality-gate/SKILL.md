---
name: quality-gate
description: "Repository-wide quality gate for meaningful code, test, configuration, dependency, and documentation changes. Use after implementing a change, before review or merge, and for release readiness."
---

# Repository Quality Gate

Run this gate for meaningful changes in either Home Assistant project. Apply the common checks below, then follow the target project's linked rules and run its own validation commands. Do not mix project environments or assume their test patterns are interchangeable.

## Gate procedure

1. **Establish scope**
   - Identify the affected project and user-visible or internal behavior changed.
   - Review the relevant diff, including existing uncommitted work; do not include or revert unrelated changes.
   - Consult that project's guidance from the [repository skill](../homeassistant-addons/SKILL.md).
2. **Check completeness**
   - Confirm relevant tests cover changed behavior and important edge cases.
   - Update directly affected documentation, translations, and configuration references.
   - Update changelog, version, dependency inventory, `sbom`, or `foss` only when the change or release process requires it; do not create release churn for routine changes.
3. **Validate**
   - Run the smallest relevant test, lint, type-check, or build command documented by the project.
   - Run broader project checks when the focused check exposes regressions or when preparing a release.
   - For Home Assistant changes, verify the affected setup, entity, service, config flow, and translation surfaces as applicable.
   - For frontend changes, use the affected project's frontend toolchain and tests.
4. **Review**
   - Inspect the final diff for unintended changes, stale references, secrets, and generated artifacts.
   - Confirm renamed `sbom`/`foss` files and all links use lowercase names.
   - Never report a check as passing unless it was actually run and passed.

## Project-specific gates

- **One.com DynDNS Updater:** follow the [One.com quality checklist](../../../onecomdyndns/.github/skills/quality-checklist/SKILL.md) for release and versioning requirements.
- **Gas & Water Meter:** follow the [Gas & Water Meter project skill](../../../gasandwater/.github/skills/gas-water-meter-project/SKILL.md) for its test commands, integration behavior, and release requirements.

## Gate result

Report one of these outcomes with the checks actually run and any remaining blockers:

- **PASS** — applicable checks passed and no material gaps remain.
- **PASS WITH GAPS** — checks passed, but a relevant check could not be run; name it and explain why.
- **FAIL** — a required check failed or a material correctness issue remains.

Do not treat skipped tests, build failures, missing tools, or unresolved release requirements as a pass.
