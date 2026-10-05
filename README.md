# MTSC 451 — Advanced Calculus I · Lecture Notes

Interactive lecture notes for **MTSC 451, Advanced Calculus I**, Delaware State University, Fall 2026.
Instructor: Abdallah Alsammani.

The site is built with [Jupyter Book 2](https://jupyterbook.org) (MyST Markdown) and published with
GitHub Pages. Planned address: <https://aalsammani.github.io/MTSC-451-Advanced-Calculus/>

## Project layout

```
index.md                 Home page
syllabus.md              Web syllabus (official PDF in downloads/)
resources.md             Texts, notation guide, downloads, list of interactive figures
module-01/               Module 1 overview + Lectures 01–07
module-02/ … module-06/  Module overview pages; new lectures go here
interactive/mathviz.mjs  The interactive figures (plain JavaScript, no dependencies)
assets/css/course.css    Site styling
assets/figures/          Figures (SVG, compiled from the TikZ code in the LaTeX notes)
downloads/               PDFs: syllabus and lecture notes
latex-source/            The LaTeX lecture notes and syllabus (the LaTeX/PDF workflow)
templates/               lecture-template.md — starting point for a new lecture
scripts/                 Helpers: new_lecture.py, build_pdfs.py, build_figures.py, serve_static.py
plugins/                 A small build plugin that keeps punctuation next to inline math
docs/                    ADDING_A_LECTURE.md, CONVERSION_AUDIT.md
myst.yml                 Site configuration and table of contents
.github/workflows/       Automatic build and deployment to GitHub Pages
```

## Preview locally

One-time setup. You need Python 3.10 or newer; Node.js is installed automatically on first run.

```bash
pip install -r requirements.txt
```

Live preview while writing (reloads on save):

```bash
jupyter-book start
```

Then open <http://localhost:3000>. If it asks to install Node.js, answer `y`.

Static build, identical to what GitHub Pages serves:

```bash
jupyter-book build --html
python scripts/serve_static.py      # then open http://localhost:8000
```

Build output goes to `_build/`, which is not committed. On OneDrive, the first build downloads
about 150 MB of website tooling into `_build/`. You can delete the folder at any time.

## Add a lecture

See [docs/ADDING_A_LECTURE.md](docs/ADDING_A_LECTURE.md). In short:

```bash
python scripts/new_lecture.py 08 2 "Functions of Several Variables"
# write module-02/lecture-08.md, preview with `jupyter-book start`, then:
git add -A && git commit -m "Add Lecture 08" && git push
```

## LaTeX / PDF workflow

The LaTeX notes remain the source for the PDF handouts:

```bash
python scripts/build_pdfs.py        # latex-source/lectures/*.tex  ->  downloads/MTSC451_Lecture_NN.pdf
python scripts/build_figures.py     # TikZ pictures                ->  assets/figures/*.svg
```

Both need a TeX distribution (MiKTeX or TeX Live).

## Deployment

Every push to `main` runs `.github/workflows/deploy.yml`. It installs Jupyter Book, builds the site,
and publishes it to GitHub Pages. One-time setting: **Settings → Pages → Source: GitHub Actions**.

## Notes on content

`docs/CONVERSION_AUDIT.md` records how the LaTeX notes were converted, the verification performed,
every correction, and the items left for the instructor's review.
