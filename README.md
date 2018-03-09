# Scibowl
This is a LaTeX-based problem manager for Scibowl created rounds.

## How does this work?

Read the **Setup** section, which deals with about setting up `scibowl.sty` with your own problem directory. `scibowl.sty` assumes you have all question files in a single folder, which I'll call the problem database.

The rest is pretty user-friendly -- follow the samples! I've included the details below, though, for reference.

### Setup
First, go into `scibowl.sty` and change the definition of `\sci` to match your own problem database. Right now, the relevant line of code reads:
```latex
\newcommand{\sci}[1]{\import{/Users/diaoeous/Documents/LaTeX/Problems/-Statement/-Scibowl/}{#1.tex}}
```
Replace `/Users/diaoeous/Documents/LaTeX/Problems/-Statement/-Scibowl/` with the directory of your problem database.

### Formatting

Advice: use the templates! They make life easier. Here's how the formatting is intended to work:

#### Rounds
Use the template [here](Templates/round-template.tex).

When using `\toss` or `\bonus`, the argument is equal to the filename (without the extension). For instance, if I wanted to include the question named `biology-1.tex` *from my problem database* as a tossup, I would enter it as `\toss{biology-1}` in the LaTeX file.

#### Short answer
Short answer question files follow the following format:
```latex
\subj{Subject}
\short
Question text

\ans{answer}
```
Ideally there should be whitespace between `Question text` and `\ans{answer}` but no whitespace between `\short` and `Question text`. See [this](Templates/short-template.tex) for a short answer template.

#### Multiple choice
Multiple choice question files follow the following format:
```latex
\subj{Subject}
\mult
Question text

\begin{enumerate}[label={\scshape \alph*)}]
    \setcounter{enumii}{22}
    \ii Answer choice W
    \ii Answer choice X
    \ii Answer choice Y
    \ii Answer choice Z
\end{enumerate}

\ans{answer}
```
Ideally there should be whitespace between `\end{enumerate}` and `\ans{answer}` but no whitespace between `\mult` and `Question text`. See [this](Templates/mult-template.tex) for a multiple choice template.

## Convenience

For reference, examples are located in the `Samples` folder in this project, and templates are located in the `Templates` folder.
