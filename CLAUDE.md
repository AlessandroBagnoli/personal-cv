# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A personal CV built with LaTeX using the [Awesome-CV](https://github.com/posquit0/Awesome-CV) template. The compiler is **XeLaTeX** (required — not pdflatex).

## Building locally

```bash
xelatex cv_eng.tex
```

Or with latexmk (mirrors what CI does):

```bash
latexmk -xelatex cv_eng.tex
```

Output: `cv_eng.pdf`

## File structure

- `cv_eng.tex` — root document: personal info header, page layout, font/color config, and `\input` directives
- `eng/summary.tex` — professional summary section
- `eng/experience.tex` — work history
- `eng/education.tex` — education
- `awesome-cv.cls` — the Awesome-CV LaTeX class (upstream template, modify with care)
- `version` — plain-text semver (`MAJOR.MINOR.PATCH`), read by CI to tag releases

## CI / Release workflow

Three GitHub Actions workflows:

| Workflow | Trigger | What it does |
|---|---|---|
| `FeaturePush.yml` | push to any branch except `main` | Compiles LaTeX to verify it builds |
| `MergeRequest.yml` | PR targeting `main` | Compiles, creates a draft release (deleted after), sends Telegram notification |
| `CreateReleaseAfterMerge.yml` | push to `main` | Compiles, tags the repo with `v<version>`, creates a GitHub release, uploads `CV_Bagnoli_Alessandro_EN.pdf`, sends Telegram notification |

**To cut a release:** bump `version`, merge to `main`. The tag must not already exist and must match `^[0-9]+.[0-9]+.[0-9]+$`.

## Versioning

The `version` file drives everything. Always update it before merging a PR to `main`, otherwise CI will fail with a duplicate-tag error.
