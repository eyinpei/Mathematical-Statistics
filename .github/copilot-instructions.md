# Copilot instructions for this repository

Purpose: Help AI coding agents be immediately productive working on this LaTeX-based course/conference repo.

- **Big picture:** This repo contains LaTeX templates and course submission notes. Major files:
  - `conference_101719.tex` — IEEEtran conference template (primary paper template).
  - `test.tex` — small xelatex + `ctex` test document demonstrating Chinese support.
  - `procedure.txt` — course submission rules (naming, deliverables, deadline).
  - `README.md` — macOS-specific LaTeX setup and VS Code `LaTeX Workshop` guidance.

- **What the agent should do first:** open the three files above to learn formatting and build expectations; treat `conference_101719.tex` as the canonical formatting example.

- **Build / dev workflow (discoverable & reproducible):**
  - This project is compiled with standard TeX tools. On macOS the repo expects MacTeX (TeX Live). Common commands:
    - `pdflatex conference_101719.tex` (single run)
    - `pdflatex -> bibtex -> pdflatex -> pdflatex` for `.bib` bibliographies
    - `xelatex test.tex` for documents that require `ctex`/Unicode (see `test.tex` header `% !TEX program = xelatex`).
  - VS Code users: repository `README.md` includes a suggested `LaTeX Workshop` settings snippet and recipes; use that when automating builds inside the editor.

- **Project-specific conventions & patterns:**
  - Use `ctex` + `xelatex` when the document includes Chinese (see `test.tex`).
  - Follow IEEE template guidance in `conference_101719.tex`: avoid `eqnarray` (use `align` or `IEEEeqnarray`), number equations consecutively and place `\\label` after captions.
  - Keep figures/tables separate until after text formatting; use `Fig.~\\ref{...}` and `\\eqref{...}` for references (per template guidance).
  - Bibliography must include `.bib` files when sharing source (the template warns that BibTeX does not work magically).

- **Integration points & external dependencies:**
  - TeX Live / MacTeX (or BasicTeX + packages) — required to compile. If BasicTeX is used, agent should note missing package errors and suggest installing via `tlmgr`.
  - Images referenced by `\\includegraphics{...}` must match filename case exactly (macOS case-sensitive filesystems are possible); prefer ASCII filenames.

- **Submission rules to preserve:**
  - From `procedure.txt`: final submission must include runnable code, environment instructions, and a PDF paper (>=6 pages) and be packaged as `组号-学号-姓名.zip`.

- **Edits the agent may perform safely:**
  - Small fixes to LaTeX sources (typos, proper `\\label` placement, switch `eqnarray`→`align`) and adding missing `\\usepackage` lines when a package is demonstrably required by code.
  - Add or update a `.bib` file if bibliography entries are missing and references are present.

- **What not to change without human confirmation:**
  - Do not alter the main IEEE formatting rules embedded in `conference_101719.tex` (margins, class options), and do not remove required template constraints unless user asks.

- **Where to look for examples:**
  - `conference_101719.tex` — paper structure, headings, and template constraints.
  - `test.tex` — example of xelatex + `ctex` usage for Chinese text.
  - `README.md` — macOS setup and VS Code LaTeX Workshop configuration snippets.

If anything above is unclear or you want more detail (build scripts, CI integration, or automated PDF checks), tell me which area to expand. 
