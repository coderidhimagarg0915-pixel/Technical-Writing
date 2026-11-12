# LaTeX – Concepts, Commands and Practical Implementation

## 1. Introduction

LaTeX is a document preparation system widely used for creating technical documents, research papers, academic reports, mathematical publications and presentations.

Unlike conventional word processors, LaTeX uses markup commands to define the structure and formatting of a document. It separates content from presentation, allowing documents to maintain consistent formatting and professional typesetting.

### 1.1 Applications of LaTeX

- Writing research papers and academic publications.
- Typesetting complex mathematical equations.
- Preparing project reports and technical documentation.
- Creating professional resumes and CVs.
- Designing presentations using Beamer.

## 2. Getting Started with LaTeX

### 2.1 Basic Document Structure

A basic LaTeX document consists of a preamble and a document environment.

```latex
\documentclass{article}

\begin{document}

Hello World!

\end{document}
```

**Explanation:**

- `\documentclass{article}` specifies the type of document.
- `\begin{document}` marks the beginning of the document body.
- `\end{document}` marks the end of the document.

### 2.2 Document Classes

The `\documentclass` command determines the overall structure of a document.

Common document classes include:

| Document Class | Purpose |
|---|---|
| article | Short articles and academic papers |
| report | Longer reports and dissertations |
| book | Books and lengthy publications |
| beamer | Presentations |

Example:

```latex
\documentclass[12pt,a4paper]{report}
```

Here:
- `12pt` specifies the font size.
- `a4paper` specifies the paper size.
- `report` specifies the document class.

### 2.3 Packages

Packages extend the functionality of LaTeX.

Packages are included in the preamble using:

```latex
\usepackage{package-name}
```

Examples:

```latex
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage{xcolor}
\usepackage{geometry}
```

### 2.4 Document Structure Commands

```latex
\section{Introduction}
\subsection{Background}
\subsubsection{Overview}

\tableofcontents
```

These commands organize content hierarchically and generate a table of contents.

---

## 3. Text Formatting and Lists

### 3.1 Text Formatting

LaTeX provides commands for changing the appearance of text.

| Command | Purpose |
|---|---|
| `\textbf{...}` | Bold text |
| `\textit{...}` | Italic text |
| `\underline{...}` | Underlined text |
| `\texttt{...}` | Monospaced text |
| `\emph{...}` | Emphasized text |

Font sizes can be changed using commands such as:

```latex
{\small Small text}
{\large Large text}
{\Large Larger text}
{\Huge Huge text}
```

### 3.2 Lists

LaTeX supports three commonly used list environments.

**A. Unordered List – itemize**

```latex
\begin{itemize}
    \item LaTeX
    \item HTML
    \item Markdown
\end{itemize}
```

**B. Ordered List – enumerate**

```latex
\begin{enumerate}
    \item Research papers
    \item Project reports
    \item Presentations
\end{enumerate}
```

**C. Descriptive List – description**

```latex
\begin{description}
    \item[Presentational] Controls document appearance.
    \item[Procedural] Provides processing instructions.
    \item[Descriptive] Identifies document elements.
\end{description}
```

---

## 4. Mathematical Typesetting

One of the major advantages of LaTeX is its ability to typeset complex mathematical expressions.

The `amsmath` package provides several useful mathematical environments.

```latex
\usepackage{amsmath}
```

### 4.1 Inline and Display Mathematics

Inline mathematics is written using `$...$` or `\(...\)`.

```latex
Einstein's equation is $E = mc^2$.
```

Display mathematics places an equation on a separate line.

```latex
\[
v = u + at
\]
```

### 4.2 Fractions and Roots

```latex
\[
x = \frac{\sqrt{a^2+b^2}}{c}
\]
```

- `\frac{a}{b}` creates a fraction.
- `\sqrt{x}` creates a square root.
- `\sqrt[n]{x}` creates an nth root.

### 4.3 Mathematical Symbols and Fonts

```latex
\[
G_{\mu\nu}+\Lambda g_{\mu\nu}=\kappa T_{\mu\nu}
\]

\[
\forall x \in \mathbb{R},\quad
\exists \epsilon > 0
\]
```

Common mathematical commands:

| Command | Output |
|---|---|
| `\alpha` | α |
| `\beta` | β |
| `\infty` | ∞ |
| `\forall` | ∀ |
| `\exists` | ∃ |
| `\sum` | Summation |
| `\int` | Integral |
| `\partial` | Partial derivative |
| `\nabla` | Nabla |

### 4.4 Summations and Calculus

```latex
\[
\sum_{k=0}^{n} {n \choose k}
\theta^k(1-\theta)^{n-k}
\]
```

```latex
\[
\int_0^1 (3x^2+2x+1)\,dx
\]
```

Partial derivatives can be represented using:

```latex
\[
\frac{\partial^2 u}{\partial x^2}
\]
```

### 4.5 Multiline Equations and Alignment

The `align` environment allows multiple equations to be aligned.

```latex
\begin{align}
x &= 5 \\
x+y &= 3
\end{align}
```

The `&` symbol specifies the alignment point, while `\\` starts a new line.

To suppress numbering:

```latex
\begin{align*}
x &= 5 \\
x+y &= 3
\end{align*}
```

### 4.6 Matrices and Arrays

LaTeX provides different matrix environments.

```latex
\[
A =
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
\]
```

Other matrix environments include:

- `matrix` – no surrounding delimiters.
- `pmatrix` – parentheses.
- `bmatrix` – square brackets.
- `vmatrix` – vertical bars.
- `Vmatrix` – double vertical bars.

The `array` environment allows custom column alignment.

```latex
\[
\begin{array}{c|cc}
x_1 & a_{11} & a_{12} \\
x_2 & a_{21} & a_{22}
\end{array}
\]
```

### 4.7 Piecewise Functions

The `cases` environment is used to represent piecewise-defined functions.

```latex
\[
f(x)=
\begin{cases}
x^2+2x+1, & x<0,\\
x+1, & 0\leq x<4,\\
x-1, & x\geq4.
\end{cases}
\]
```

### 4.8 Overbraces and Underbraces

These commands annotate mathematical expressions with explanatory labels.

```latex
\[
\overbrace{a+b+c}^{\text{First Group}}
+
\underbrace{x+y+z}_{\text{Second Group}}
\]
```

They are useful for identifying different components of a mathematical expression.

---

## 5. Tables and Advanced Tabular Formatting

LaTeX supports structured tables through the `tabular` and `table` environments.

### 5.1 Basic Tables

```latex
\begin{tabular}{|c|c|c|}
\hline
\textbf{Roll No.} & \textbf{Name} & \textbf{CGPA} \\
\hline
101 & Amit & 8.45 \\
102 & Neha & 9.12 \\
\hline
\end{tabular}
```

Column alignment:
- `l` – left alignment.
- `c` – center alignment.
- `r` – right alignment.
- `|` – vertical border.

### 5.2 Multicolumn

The `\multicolumn` command combines multiple columns into one cell.

```latex
\begin{tabular}{|c|c|c|}
\hline
\multicolumn{3}{|c|}{Academic Performance} \\
\hline
Student & Midterm & Final \\
\hline
A & 78 & 89 \\
B & 85 & 92 \\
\hline
\end{tabular}
```

### 5.3 Multirow

The `multirow` package allows a cell to span multiple rows.

```latex
\usepackage{multirow}

\begin{tabular}{|c|c|}
\hline
\multirow{2}{*}{CSE} & Data Structures \\
                     & Machine Learning \\
\hline
\end{tabular}
```

### 5.4 Colored Tables

The `xcolor` and `colortbl` packages support table coloring.

```latex
\usepackage[table]{xcolor}

\begin{tabular}{|c|c|}
\hline
\rowcolor{gray!30}
\textbf{Student} & \textbf{Marks} \\
\hline
Amit & 92 \\
Neha & 85 \\
\hline
\end{tabular}
```

Custom colors can be defined using RGB values.

```latex
\definecolor{custompurple}{RGB}{200,20,200}
```

The `\colorlet` command can define a color using a mixture of existing colors.

```latex
\colorlet{customcolor}{red!60!yellow}
```

### 5.5 Fixed-Width Columns

The `p{width}` column specification allows paragraphs to wrap inside table cells.

```latex
\begin{tabular}{|p{3cm}|p{5cm}|}
\hline
Technique & Description \\
\hline
Pruning & Removes unnecessary parameters from a neural network. \\
\hline
\end{tabular}
```

### 5.6 Professional Tables Using Booktabs

The `booktabs` package provides professional horizontal rules.

```latex
\usepackage{booktabs}

\begin{tabular}{lccc}
\toprule
Model & Parameters & FLOPs & Accuracy \\
\midrule
ResNet18 & 11.7M & 1.82G & 94.21\% \\
MobileNetV2 & 3.5M & 0.30G & 92.84\% \\
\bottomrule
\end{tabular}
```

Important commands:
- `\toprule`
- `\midrule`
- `\bottomrule`

Unlike traditional bordered tables, professional booktabs tables generally avoid vertical lines.

### 5.7 Nested Tables and Mathematical Expressions

LaTeX also allows tables inside table cells and mathematical expressions inside tabular environments.

These techniques are useful when presenting structured scientific data, model comparisons and technical results.

---

## 6. Colors, Figures and Images

### 6.1 Color Representation

Colors can be specified using different models, including RGB and HTML hexadecimal notation.

```latex
\usepackage{xcolor}

\definecolor{custompurple}{RGB}{200,20,200}
\definecolor{customblue}{HTML}{3366CC}
```

Text can be colored using:

```latex
\textcolor{custompurple}{Colored Text}
```

A mathematical expression can also be colored:

```latex
\[
\textcolor{custompurple}{T(n)=aT(n/b)+f(n)}
\]
```

### 6.2 Inserting Images

The `graphicx` package is used for inserting images.

```latex
\usepackage{graphicx}
```

Example:

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.5\textwidth]{image.png}
    \caption{Sample Image}
    \label{fig:sample}
\end{figure}
```

### 6.3 Image Rotation and Cropping

The `angle` option rotates an image.

```latex
\includegraphics[width=0.4\textwidth,angle=90]{logo.png}
```

Cropping can be performed using `trim` and `clip`.

```latex
\includegraphics[
    width=\textwidth,
    trim=0cm 1cm 0cm 2cm,
    clip
]{building.png}
```

The trim values represent left, bottom, right and top, respectively.

### 6.4 Multiple Images Using Minipages

The `minipage` environment allows multiple blocks to be placed side by side.

```latex
\begin{figure}[h]
\centering

\begin{minipage}{0.45\textwidth}
    \centering
    \includegraphics[width=\textwidth]{image1.png}
    \caption{First Image}
\end{minipage}
\hfill
\begin{minipage}{0.45\textwidth}
    \centering
    \includegraphics[width=\textwidth]{image2.png}
    \caption{Second Image}
\end{minipage}

\end{figure}
```

---

## 7. Reports and Document Design

The `report` document class is suitable for longer academic documents.

### 7.1 Title Page

```latex
\documentclass[12pt,a4paper]{report}

\begin{document}

\begin{titlepage}
\centering
{\Huge\bfseries Introduction to LaTeX\par}
\vspace{1cm}
{\Large Student Name\par}
\vspace{0.5cm}
Course: Technical Writing

\end{titlepage}

\end{document}
```

### 7.2 Abstract and Chapters

```latex
\begin{abstract}
This document introduces the fundamentals
of LaTeX and its applications.
\end{abstract}

\chapter{Introduction}
\section{Background}
\subsection{Overview}
```

### 7.3 Custom Heading Styles

The `sectsty` package can customize section heading appearances.

```latex
\usepackage{sectsty}
\usepackage{xcolor}

\chapterfont{\color{red}\bfseries\Huge}
\sectionfont{\color{magenta}\itshape\Large}
\subsectionfont{\color{orange}}
```

### 7.4 Headers and Footers

The `fancyhdr` package provides control over page headers and footers.

```latex
\usepackage{fancyhdr}

\pagestyle{fancy}
\fancyhf{}

\lhead{Student Name}
\chead{Technical Writing}
\rhead{\today}

\cfoot{\thepage}
```

---

## 8. Advanced Document Structure

### 8.1 Font Families

The `fontspec` package allows the use of system fonts when compiling with XeLaTeX or LuaLaTeX.

```latex
\usepackage{fontspec}

\setmainfont{DejaVu Serif}
\setsansfont{DejaVu Sans}
\setmonofont{Courier New}
```

Different font families can be selected using:

```latex
{\rmfamily Serif Text}

{\sffamily Sans-serif Text}

{\ttfamily Monospace Text}
```

**Important:** Documents using `fontspec` must be compiled using XeLaTeX or LuaLaTeX, rather than pdfLaTeX.

### 8.2 Background Colors

The `xcolor` package supports background coloring.

```latex
\usepackage{xcolor}

\pagecolor{yellow!10}
```

### 8.3 Spacing and Paragraph Formatting

LaTeX provides commands for controlling paragraph spacing and line breaks.

```latex
First line of a paragraph.\\
Another line in the same paragraph.

\vspace{1cm}

This paragraph starts 1cm below.
```

The `\vspace` command introduces vertical space.

### 8.4 Hyphenation

LaTeX automatically breaks long words when required to maintain proper text alignment.

Manual hyphenation can be specified using:

```latex
\hyphenation{in-com-pre-hen-si-bil-i-ties}
```

### 8.5 Section Numbering

Section numbering can be customized.

For example, alphabetic section numbering:

```latex
\renewcommand{\thesection}{\Alph{section}}
```

Equation numbering can be managed using equation environments.

```latex
\begin{equation}
x^2+y^2=1
\end{equation}
```

### 8.6 Boxes and Saveboxes

LaTeX provides boxes for storing and arranging content.

```latex
\newsavebox{\mybox}

\savebox{\mybox}{This message is written in a savebox.}

\usebox{\mybox}
```

The `\parbox` command creates a fixed-width paragraph box.

```latex
\parbox{5cm}{
This message is wrapped in a 5cm paragraph box.
}
```

### 8.7 Index Generation

An index helps readers locate important terms in a document.

The `makeidx` package is used to generate an index.

```latex
\usepackage{makeidx}
\makeindex
```

Mark terms within the document:

```latex
LaTeX\index{LaTeX}
```

Print the index:

```latex
\printindex
```

The index requires an additional indexing compilation step.

### 8.8 Bibliography Management Using BibTeX

BibTeX helps manage references separately from the main LaTeX document.

A bibliography entry can be stored in a `.bib` file.

Example:

```bibtex
@article{einstein1905,
    author = {Albert Einstein},
    title = {On the Electrodynamics of Moving Bodies},
    year = {1905}
}
```

The `natbib` package supports citation commands.

```latex
\usepackage{natbib}

\citet{einstein1905}
\citep{einstein1905}
```

The bibliography can be included using:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

The bibliography style determines how references are formatted.

---

## 9. Important Packages Reference

| Package | Purpose |
|---|---|
| amsmath | Mathematical typesetting |
| amssymb | Additional mathematical symbols |
| graphicx | Image insertion and manipulation |
| xcolor | Color definitions and text coloring |
| colortbl | Table coloring |
| multirow | Cells spanning multiple rows |
| booktabs | Professional table formatting |
| geometry | Page dimensions and margins |
| sectsty | Custom section headings |
| fancyhdr | Headers and footers |
| fontspec | System font selection with XeLaTeX/LuaLaTeX |
| natbib | Citation management |
| makeidx | Index generation |
| hyperref | Hyperlinks and PDF navigation |

---

## 10. Practical Implementation – Resume Creation

As a practical application of the concepts learned, a professional resume was created using LaTeX.

The project demonstrates:

- Document structure and formatting.
- Package management.
- Custom commands.
- Section headings and lists.
- Tables and alignment.
- Hyperlinks.
- PDF generation.

### Project Files

| File | Description |
|---|---|
| `ridhima_resume.tex` | LaTeX source code |
| `ridhima_resume.pdf` | Compiled resume |
| `README.md` | Documentation of the practical |

### Compilation

The resume was developed and compiled using Overleaf.

1. Create a new Overleaf project.
2. Upload the `.tex` source file.
3. Set the correct main document.
4. Compile the document.
5. Download the generated PDF.

---

## 11. Learning Outcomes

Through these practical assignments, the following concepts were explored:

- Understanding the fundamentals and structure of LaTeX documents.
- Creating structured academic documents using document classes and environments.
- Typesetting mathematical equations, matrices and scientific expressions.
- Designing tables with advanced formatting and color customization.
- Inserting, positioning, rotating and cropping images.
- Creating reports with customized headings, headers and footers.
- Working with fonts, spacing, boxes and document numbering.
- Managing citations, bibliographies and indexes.
- Applying LaTeX concepts to create a professional resume.

---

**Note:** This documentation is based on the concepts and practical exercises covered in the Technical Writing classes.