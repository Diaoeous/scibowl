# Scibowl
This is a LaTeX-based problem manager for Scibowl created rounds.

## How does this work?

`scibowl.sty` is intended to make compiling Scibowl rounds more convenient through a few optimizations.
* The main optimization is **storing problems in a single folder**.
    * `scibowl.sty` operates under the assumption that a single folder (which I'll refer to as the *problem database*) contains all question files.
    * This has a few benefits:
        * faster problem lookup
        * less text to handle in round compilation
        * simplified inclusion in rounds
* `scibowl.sty` **does the formatting for you**.
    * No need for manually numbering problems, inserting horizontal separators, placing answers in all caps, etc. etc...
    * All formatting is done for you by `scibowl.sty`. Just follow the templates!

Read the **Setup** section, which deals with setting up `scibowl.sty` with your own problem database.

The rest is pretty user-friendly -- follow the templates! I've included the details below, though, for reference.

### Setup
First, go into `scibowl.sty` and change the definition of `\pdatabase` to match your own problem database. Right now, the relevant line of code reads:
```latex
\newcommand{\pdatabase}{/Users/diaoeous/Documents/LaTeX/Problems/-Statement/-Scibowl/}
```
Replace `/Users/diaoeous/Documents/LaTeX/Problems/-Statement/-Scibowl/` with the directory of your problem database.

### Formatting

Advice: **use the templates**! They make life easier. Here's how the formatting is intended to work:

#### Rounds
Use the template [here](Templates/round-template.tex).

`scibowl.sty` has two options: `folder` and `nofolder`. `folder` is the default option, which requires two parameters for `\toss` and `\bonus` and is used when importing problems from a folder *within* your problem database. If your problems are not enclosed in any folders within your problem database, use `nofolder` instead with the line
```latex
\usepackage[nofolder]{scibowl}
```

**If using `folder`**: `\toss` and `\bonus` both require two parameters, the first of which is the enclosing folder name and the second of which is the file name. For instance, if I wanted to include the question named `1.tex` from folder `biology` as a tossup, I would enter it in as `\toss{biology}{1}`.

**If using `nofolder`**: when using `\toss` or `\bonus`, the argument is equal to the filename (without the extension). For instance, if I wanted to include the question named `biology-1.tex` *directly from my problem database* as a tossup, I would enter it as `\toss{biology-1}` in the LaTeX file.

#### Short answer
See [this](Templates/short-template.tex) for a short answer template.

Short answer question files follow the following format:
```latex
\subj{Subject}
\short
Question text

\ans{answer}
```
Ideally there should be whitespace between `Question text` and `\ans{answer}` but no whitespace between `\short` and `Question text`. 

#### Multiple choice
See [this](Templates/mult-template.tex) for a multiple choice template.

Multiple choice question files follow the following format:
```latex
\subj{Subject}
\mult
Question text

\begin{enumerate}[label={\scshape \alph*)}]
    \setcounter{enumii}{22}
    \ii answer choice W
    \ii answer choice X
    \ii answer choice Y
    \ii answer choice Z
\end{enumerate}

\ans{y) answer choice Y}
```
Ideally there should be whitespace between `\end{enumerate}` and `\ans{answer}` but no whitespace between `\mult` and `Question text`.

## Convenience

For reference, templates are located in the `Templates` folder of this project and examples are located in the `Samples` folder. For the lazy:

### Templates
* [Round template](Templates/round-template.tex)
* [Multiple choice template](Templates/mult-template.tex)
* [Short answer template](Templates/short-template.tex)

### Examples
* [Sample round](Samples/sample-round.tex) ([PDF output](Samples/sample-round.pdf))
* [Multiple choice example](Samples/mult-example.tex)
* [Short answer example](Samples/short-example.tex)
