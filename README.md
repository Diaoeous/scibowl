# Scibowl
This is a LaTeX-based problem manager for Scibowl created rounds.

## How does this work?
First, go into `scibowl.sty` and change the definition of `\sci` to match your own problem directory.

When using `\toss` or `\bonus`, the argument is equal to the filename (without the extension). For instance, if I wanted to include the question named `biology-1.tex` as a tossup, I would enter it as `\toss{biology-1}` in the LaTeX file.

The rest is pretty user-friendly -- follow the samples! They should be pretty self-explanatory.
