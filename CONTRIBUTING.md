# Contributing

Reponomics Dashboard Action is in a public pre-release hardening period. The repository is visible so its security posture, workflows, dependency handling, and release process can be reviewed in the open, but it is not yet being promoted for general use.

Security reports are welcome. For security issues, follow `SECURITY.md` instead of opening a public issue with exploit details.

## Current Contribution Policy <>

Issues and pull requests that are most likely to be useful during pre-release:

- security vulnerability reports submitted through the private reporting path;
- small corrections to inaccurate documentation;
- reproducible CI, packaging, or release-process failures;
- narrowly scoped fixes for behavior that is already documented.

Please do not submit speculative integrations, large rewrites, new product features, formatting-only changes, or dependency churn unless a maintainer has asked for them.

## Windows

This project uses GNU Make, which is not included with Windows by default. The setup commands below should be run from an MSYS2 shell rather than PowerShell or Command Prompt.

Before running the setup commands below, install Make using one of these options.

With Chocolatey, run the following command from an elevated PowerShell session:

```powershell
choco install make
```

After installation, close and reopen your MSYS2 shell so it receives the updated `PATH`.

Alternatively, install Make directly from an MSYS2 shell:

```bash
pacman -S make
```

From the MSYS2 shell that you will use for development, verify that Make is available:

```bash
make --version
```

Run all of the Make commands in the following sections from that same MSYS2 shell.

## Development Setup

Use the project Makefile for local development. The repository expects a local `venv` virtual environment.

```bash
make install
make pre-commit-install
make ci
```

Individual checks are named after what they do:

```bash
make lint
make type-check
make validate
make test
make coverage
```

Focused fixture checks are also available:

```bash
make fixture-collect
make fixture-publish
make fixture-rotate-key
```

Do not commit generated local state such as `venv`, coverage reports, caches, rendered dashboard output, or local dashboard data artifacts.

## Markdown Formatting

Do not hard-wrap Markdown prose. Keep paragraphs as single logical lines so future edits produce smaller diffs. The `LICENSE` file is the exception and may keep conventional license-text wrapping.
