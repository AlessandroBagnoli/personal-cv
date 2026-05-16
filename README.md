# personal-cv [![Github Actions](https://github.com/AlessandroBagnoli/personal-cv/actions/workflows/CreateReleaseAfterMerge.yml/badge.svg)](https://github.com/AlessandroBagnoli/personal-cv/actions/workflows/CreateReleaseAfterMerge.yml) [![CV Eng](https://img.shields.io/badge/ENG-PDF-green.svg)](https://github.com/AlessandroBagnoli/personal-cv/releases/latest/download/CV_Bagnoli_Alessandro_EN.pdf)

Personal Curriculum Vitae built with LaTeX. Download the latest PDF from [**here**](https://github.com/AlessandroBagnoli/personal-cv/releases/latest).

## Build locally

Requires XeLaTeX.

```bash
xelatex cv_eng.tex
```

## Structure

```
cv_eng.tex          # Root document — personal info, layout, font/color config
eng/summary.tex     # Professional summary
eng/experience.tex  # Work history
eng/education.tex   # Education
version             # Semver string used by CI to tag releases
```

## Releases

Merging to `main` triggers a GitHub Actions workflow that compiles the PDF, tags the repo with the version in `version`, and publishes a GitHub release. Bump `version` before every merge to `main`.

## Credits

- [**LaTeX**](https://www.latex-project.org) — typesetting system
- [**Awesome-CV**](https://github.com/posquit0/Awesome-CV) — LaTeX CV template
- [**latex-action**](https://github.com/xu-cheng/latex-action) — GitHub Action to compile LaTeX