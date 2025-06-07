# 📄 Final Article – ATOM Project

This folder contains all files related to the final scientific article.

## Structure

- `main.tex`: Main LaTeX file.
- `sections/`: Article sections split into separate `.tex` files.
- `images/`: All figures and diagrams used in the paper.
- `references.bib`: Bibliography file in BibTeX format.
- `output/`: PDF versions of each article version or submission.
- `README.md`: This file – provides compilation instructions and folder structure.

## Compilation

To compile the article, run:
```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
