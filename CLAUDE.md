# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Build

```bash
latexmk -pdf resume.tex 
```

The `.gitignore` excludes all LaTeX auxiliary files and the compiled PDF.

## Structure

This is a LaTeX resume. The entry point is `resume.tex`, which stitches together modular section files via `\input{}`.

- **`commands.tex`** — all custom macros. Edit here to change formatting globally.
- **`work/*.tex`** — one file per job, included in reverse-chronological order in `resume.tex`.
- **`education.tex`** — education entries.

## Custom commands

Defined in `commands.tex`:

| Command | Args | Purpose |
|---|---|---|
| `\resumesection{title}` | 1 | Top-level section heading |
| `\job{org}{title}{dates}{phone}{address}` | 5 | Job subsection heading |
| `\jobitemliststart` / `\jobitemlistend` | — | Wrap bullet list |
| `\jobitem{text}` | 1 | Single bullet |
| `\jobend` | — | Close a job block |
| `\education{institution}{degree}{year}` | 3 | Education subsection |

To add a new job, create `work/<slug>.tex` using the `\job` / `\jobitemliststart` / `\jobitem` / `\jobitemlistend` / `\jobend` pattern, then add `\input{work/<slug>.tex}` at the desired position in `resume.tex`.
