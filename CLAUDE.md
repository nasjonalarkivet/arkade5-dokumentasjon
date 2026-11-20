# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Sphinx documentation (in Norwegian, `nb_NO`) for Arkade 5, Nasjonalarkivet's test tool
for archival extracts. Published at https://docs.arkade.nasjonalarkivet.no via Read the
Docs (configured in `.readthedocs.yaml`). There is no application code here — only
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
pinned dependencies in `requirements.txt` (`sphinx`, `sphinx-rtd-theme`, `docutils`).
Note: the local, git-ignored `.venv/` was created on Windows (`Scripts/` layout) and
does not work from WSL/Linux — create a fresh venv if needed.

## Git workflow

`develop` is the working branch. `main` is the mainline: each Arkade release
reaches it through a pull request from `develop` titled "Update documentation
for Arkade 5 version X.Y.Z", merged with a merge commit (the only method the
repository ruleset on `main` allows). The merge commit is tagged `X.Y.Z` (no
`v` prefix), and new tags must be activated by hand in Read the Docs. Read the
Docs builds `latest` from `main`.

`master` is frozen. It is still GitHub's default branch because only
Nasjonalarkivet's organization admins can change that, and their ruleset
protects whichever branch is the default.

Commits in a release carry the Jira key of the release-preparation issue
(e.g. "Forberede utgivelse av Arkade X.Y.Z") as the message body.
