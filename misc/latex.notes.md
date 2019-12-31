## Formating 

Command           Declaration version     Meaning
--------         ---------------------   --------
`\textrm{}`       `\rmfamily`             roman family
`\textsf{}`       `\sffamily`
`\texttt{}`       `\ttfamily`
`\textbf{}`       `\bfseries`
`\textmd{}`       `\mdseries`
`\textit{}`       `\itshape`
`\textsl{}`       `\slshape`
`\textsc{}`       `\scshape`
`\textup{}`       `\upshape`
`\textnormal{}`   `\normalfont`

- `\noindent` suppresses the paragraph indentation
- Instead of using **groups** (`{...}`) that define a scope, we can use the
environment version of it eg. `\huge` declaration has the `\begin{huge}`
environment\
  Using environments can make the source more readable
- space vertically using `\smallskip` and `\bigskip`
- commonly adviced to end a paragraph before a font size change. as TeX
calculates interline spacing depending on the font size.
- make your own commands/macros:\
  `\newcommand{\TUG}{\emph{\textbf{\TeX\ Users Group}}\xspace}`

