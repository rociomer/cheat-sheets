### Useful commands for using LaTeX

Although I mostly use Overleaf for creating documents using LaTeX, there are some things which Overleaf does not support (at the moment). As such, you might need to install a local version.

---

For installing [texlive](https://www.tug.org/texlive/):

```
sudo apt-get install texlive
```

For installing certain packages (like algorithm2e), need to explicitely type:

```
sudo apt-get install texlive-science
```

---

To compare two documents using [latexdiff](https://ctan.org/tex-archive/support/latexdiff):

```
latexdiff draft.tex revision.tex > diff.tex
```

Then compile the difference file using:

```
pdflatex diff.tex
```

This is a bit buggy and doesn't always work so smoothly. To get it to work you sometimes have to debug the issues that arise in pdflatex. Also, sometimes the easiest thing is to remove the problematic parts of the tex file (e.g. any complex tables can be problematic) and try to recompile again with a partially complete document.

---

Another cool document processor for working with TeX/LaTeX using a graphical interface is [LyX](https://www.lyx.org/).
