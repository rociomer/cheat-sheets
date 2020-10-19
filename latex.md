### Useful commands for using LaTeX

For installing LaTeX:

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

(This is a bit buggy and doesn't always work so smoothly).
