# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Sphinx documentation (in Norwegian, `nb_NO`) for Arkade 5, Arkivverket's test tool for
archival extracts. Published at https://arkade.arkivverket.no via Read the Docs
(configured in `.readthedocs.yaml`). There is no application code here — only
reStructuredText sources.

## Structure

All content lives in the repo root as `.rst` files, wired together by the toctree in
`index.rst`:

- `Installasjonsveiledning.rst` — installation guide
- `Brukerveiledning.rst` — user guide
- `Systemdokumentasjon.rst` — system documentation
- `Versjonshistorikk.rst` — links to GitHub releases

Images go in `img/`. Project metadata (`version`, `release`, `copyright`) is set in
`conf.py` and must be bumped when a new Arkade version is released — this is the most
common change in the repo's history.

## Building

```
make html        # build HTML into _build/html
make linkcheck   # verify external links
make clean       # remove _build
```

`make.bat` provides the same targets on Windows. Requires `sphinx-build` with the
dependencies in `requirements.txt` (`docutils`, `sphinx-rtd-theme`). Note: the checked-in
`.venv/` was created on Windows (`Scripts/` layout) and does not work from WSL/Linux —
create a fresh venv if needed.

## Git workflow

`develop` is the working branch; `master` is the default branch used for PRs and what
Read the Docs publishes from.
