## Compiling

### markdown

`pandoc -H ~/.config/header -f markdown+raw_tex+raw_attribute -o pdf/out.pdf in.md`


Contents of `header`
```
\usepackage{graphicx, xcolor}
\usepackage{pstricks}
\usepackage{import}
```
