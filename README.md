# Home Assistant Add-ons

This repository contains two independent Home Assistant projects:

- [One.com DynDNS Updater](./onecomdyndns/README.md) in `onecomdyndns/`
- [Gas & Water Meter](./gasandwater/README.md) in `gasandwater/`

Each project keeps its own add-on and integration files, dependencies, tests, and
documentation. Run commands from the corresponding project directory; do not
install dependencies into a shared environment.

## Add the repository to Home Assistant

Add `https://github.com/ulfwuestefeld/homeassistant-addons` as an add-on
repository. Both add-ons are then available from this repository.

Existing installations remain associated with the repository URL they were
installed from. Adding this repository does not migrate or replace those
installations.

## Tests

One.com DynDNS:

```powershell
Set-Location onecomdyndns
python -m pip install -r requirements.txt
python -m pytest
```

Gas & Water Meter:

```powershell
Set-Location gasandwater
python -m pip install -r requirements_test.txt
python -m pytest tests/ -q
```

Gas & Water Meter frontend:

```powershell
Set-Location gasandwater/frontend-src
npm ci
npm test
```
