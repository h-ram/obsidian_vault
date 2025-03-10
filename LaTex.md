LaTeX (pronounced “_LAY_-tek” or “_LAH_-tek”) is a tool for [[Definitions#typesetting|typesetting]] professional-looking documents.
LaTex is different from those [[Definitions#wysiwyg|WYSIWYG]] tools like Microsoft office or Libre Office.
LaTeX file is processed by a piece of software called a _TeX engine_ which uses the commands embedded in your text file to guide and control the typesetting process, converting the LaTeX commands and document text into a professionally typeset PDF file.
Latex files end with `.tex` file extension.

Every LaTeX document follows a standard structure:
```tex
\documentclass{class} 
% Preamble: packages and custom settings 
\begin{document} 
% Content goes here 
\end{document}
```
* ***`\documentclass`**: Specifies the document type (e.g., `article`, `report`, `book`, `beamer` for presentations).
* **Preamble**: Contains commands to customize the document, such as importing packages.
* **`\begin{document}` and `\end{document}`**: Define the main content area, and everything between these is called the ***body***, and it is what shows in the final document.

```tex
\textbf{this text is bold, bf stands for boldface}
\textit{this text is italic}
\underline{this text is italic}
```

```tex
\section{Title}
\subsection{Subtitle}
\subsubsection{Sub-subtitle}
```

```tex
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}
```

```tex
\begin{enumerate}
    \item First item
    \item Second item
\end{enumerate}
```

```tex
\usepackage{graphicx} % Add this to the preamble 
\includegraphics[width=\linewidth]{filename}
```

```tex
\begin{tabular}{|c|c|} 
	\hline 
	Column 1 & Column 2 \\ 
	\hline 
	Data 1 & Data 2 \\ 
	\hline 
\end{tabular}
```

## Text Alignment
```tex
\begin{flushleft}
Left-aligned text.
\end{flushleft}

\begin{flushright}
Right-aligned text.
\end{flushright}

\begin{center}
Centered text.
\end{center}
```
## Footnotes
```tex
this is a foot note \footnote{Footnote text here.}
```
## Font
The default font for LaTeX is **Computer Modern**, designed by Donald Knuth, the creator of TeX.
## Comments
comments in LaTex are generate with a percent sign `%`
```tex
\begin{document}
% this line is a comment
% comments are ignored code
\end{document}
```
## Table of Contents
To insert a table of contents we use `\tableofcontents` command, which will looks for `\section{}` and `\subsection{}` commands and consider them headers in the table of contents.
```tex
\begin{document}
\tableofcontent
\section{Intro :<}
\end{document}
```
## Modularization
- In order to organize your LaTex Project, You can divide chapters sections of the your document into separate `.tex` files and import them in the main file.
- Importing can be done with two different commands `\input{filename}` or `\include{filename}`, where `filename` is the relative of absolute path to the LaTex file without typing `.tex`  at the end.
- The contents of `filename` will be dumped at the point where `\input` or `\include` was mentioned.

| `\include`           | `\input`                 |
| -------------------- | ------------------------ |
| starts on a new page | doesn't start a new page |
| resets counters      | doesn't reset counters   |
- In the preamble you can specify which imports to ignore using `\includeonly{file_1,file_2}` , mostly used for debugging.
```tex
\includeonly{chapter_1,chapter_3}
\begin{document}
\include{chapter_1}
\include{chapter_2} % this will not compile.
\include{chapter_3}
\end{document}
```
## Hyperlinks
Use the `\href` command from the `hyperref` package:
1. Add the `hyperref` package in the preamble:
```latex
\usepackage{hyperref}
```
2. Use the `\href` command in your document:
```latex
\href{https://example.com}{Your Text Here}
```
## Counters
In LaTeX, **counters** are variables that control the numbering of various elements in a document, such as sections, subsections, figures, tables, equations, and more. They allow LaTeX to automatically number these elements and keep the numbering consistent.
#### **How Counters Work**
1. **Name of Counters:** Each numbered element has an associated counter. Common counters include:
    - `section`, `subsection`, `subsubsection`: For sections and subsections.
    - `figure`: For figures.
    - `table`: For tables.
    - `equation`: For equations.
2. **Default Behavior:**
    - LaTeX automatically increments counters for each new numbered element.
    - Counters are typically hierarchical. For example, `subsection` is nested within `section`, so its numbering resets when a new section begins.
#### **Manipulating Counters**
1. **Manually Setting a Counter Value** You can set the value of a counter using the `\setcounter` command:
    ```latex
    \setcounter{counter_name}{value}
    ```
    #### Example:
    ```latex
    \setcounter{section}{3} % Starts section numbering at 4
    \section{New Section}   % Appears as "Section 4"
    ```
2. **Incrementing or Decrementing a Counter** Use the `\addtocounter` or `\stepcounter` commands:
    - `\addtocounter{counter_name}{value}`: Adds a specific value to the counter.
    - `\stepcounter{counter_name}`: Increments the counter by 1.
    #### Example:
    ```latex
    \addtocounter{section}{1} % Adds 1 to the current section number
    \stepcounter{section}     % Increments the section counter by 1
    ```
3. **Accessing Counter Values** To display the current value of a counter, use:
    ```latex
    \thecountername % change countername e.g thesection, thefigure
    ```
    #### Example:
    ```latex
    Section \thesection: This is the current section.
    ```
#### **Customizing Numbering**
You can redefine how counters are displayed using `\renewcommand`.
#### Example:
```latex
\renewcommand{\thesection}{\Roman{section}} % Use Roman numerals for sections
```
Common formatting options:
- `\arabic{counter}`: Regular numbers (1, 2, 3).
- `\roman{counter}`: Lowercase Roman numerals (i, ii, iii).
- `\Roman{counter}`: Uppercase Roman numerals (I, II, III).
- `\alph{counter}`: Lowercase letters (a, b, c).
- `\Alph{counter}`: Uppercase letters (A, B, C).
---
### **Examples of Counters in Action**
#### Resetting Subsection Numbers:
By default, subsection numbers reset when a new section begins. You can customize this behavior:
```latex
\documentclass{article}

\begin{document}

\section{First Section}
\subsection{First Subsection}  % Numbered as 1.1
\subsection{Second Subsection} % Numbered as 1.2

\section{Second Section}
\setcounter{subsection}{0}      % Reset subsection counter manually
\subsection{First Subsection}   % Numbered as 2.1

\end{document}
```
#### Numbering Figures and Tables:
```latex
\documentclass{article}

\begin{document}

\setcounter{figure}{5} % Start figure numbering at 6
\begin{figure}
\caption{A sample figure.} % Numbered as Figure 6
\end{figure}

\end{document}
```
---
### **List of Built-In Counters**
- `part`, `chapter`, `section`, `subsection`, `subsubsection`, `paragraph`, `subparagraph`
- `figure`, `table`, `equation`
- `page`: Current page number.
- `footnote`: Footnote numbering.
- `enumi`, `enumii`, `enumiii`, `enumiv`: For levels in `enumerate`.
---
###  **Suppress Counters**
There are two ways to suppress counters
#### 1. locally 
using an asterisk, e.g :`\section*` (the asterisk removes numbering). But this will prevent the section from being added to table of contents (TOC). We can use `\addcontentsline{toc}{section}{nameofsection}` to reverse that effect.
```latex
\section*{Introduction}
\addcontentsline{toc}{section}{Introduction} % Add the unnumbered section to the TOC
```
- Use `\section*` instead of `\section` for unnumbered sections.
- Add the section manually to the table of contents using `\addcontentsline`.
---
#### 2. globally
To remove numbering globally for all sections, subsections, etc., redefine the sectioning commands to exclude numbers.
#### Example:

```latex
\documentclass{article}
\usepackage{hyperref}

\setcounter{secnumdepth}{0} % Turn off section numbering

\begin{document}

\tableofcontents

\section{Introduction}
\section{Background}

\end{document}
```
- The `\setcounter{secnumdepth}{0}` command disables numbering for all section levels.
---
## Tables
Tables in LaTeX are created using the `tabular` environment, which is highly customizable. Below is a detailed guide on how to create and format tables in LaTeX.
### **Basic Table Structure**
```latex
\begin{tabular}{|c|c|c|}
\hline
Column 1 & Column 2 & Column 3 \\ 
\hline
Data 1   & Data 2   & Data 3   \\
Data 4   & Data 5   & Data 6   \\
\hline
\end{tabular}
```
- `|c|c|c|`: Specifies three centered (`c`) columns with vertical lines (`|`) between them.
- `\hline`: Adds a horizontal line.
- `\\`: Ends a row and starts a new one.
```sql
+---------+---------+---------+
| Column 1 | Column 2 | Column 3 |
+---------+---------+---------+
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
+---------+---------+---------+
```
---
### **Adding Captions and Labels**
To add a caption and make your table referencable, wrap the `tabular` environment in a `table` environment.

```latex
\begin{table}[h!]
\centering
\begin{tabular}{|l|c|r|}
\hline
Left Align & Center Align & Right Align \\ 
\hline
Text 1     & Text 2       & Text 3       \\
Text 4     & Text 5       & Text 6       \\
\hline
\end{tabular}
\caption{A sample table.}
\label{tab:sample}
\end{table}
```

- `\caption{}`: Adds a caption below the table.
- `\label{}`: Creates a label for referencing (e.g., `\ref{tab:sample}`).
- `|l|c|r|`: Specifies column alignment:
    - `l`: Left-aligned.
    - `c`: Center-aligned.
    - `r`: Right-aligned.

---

### **Merging Columns and Rows**

#### **Merging Columns (`\multicolumn`)**

Use the `\multicolumn` command to merge cells across columns.

```latex
\begin{tabular}{|c|c|c|}
\hline
\multicolumn{3}{|c|}{Merged Header} \\ 
\hline
Column 1 & Column 2 & Column 3 \\ 
\hline
Data 1   & Data 2   & Data 3   \\ 
\hline
\end{tabular}
```

- `\multicolumn{3}{|c|}{Merged Header}`: Merges three columns and centers the text within a bordered cell (`|`).

#### **Merging Rows**

Use the `multirow` package for row merging.

```latex
\usepackage{multirow}
...
\begin{tabular}{|c|c|c|}
\hline
\multirow{2}{*}{Merged Row} & Data 2 & Data 3 \\ 
                            & Data 5 & Data 6 \\ 
\hline
\end{tabular}
```

- `\multirow{2}{*}{Merged Row}`: Merges two rows for the first column.

---

### **Adding Horizontal and Vertical Spacing**

#### **Horizontal Spacing**

Use `@{}` to adjust column spacing.

```latex
\begin{tabular}{c@{\hspace{1cm}}c}
A & B \\ 
1 & 2 \\
\end{tabular}
```

#### **Vertical Spacing**

Use `\arraystretch` to adjust row height.

```latex
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{|c|c|}
A & B \\
1 & 2 \\
\end{tabular}
```

---

### **Table with Borders**

Add borders using `\hline` and `|`:

```latex
\begin{tabular}{|c|c|c|}
\hline
Header 1 & Header 2 & Header 3 \\
\hline
Data 1   & Data 2   & Data 3   \\
\hline
\end{tabular}
```

---

### **Wide and Long Tables**

#### **Wide Tables**

Use the `tabularx` package for tables that automatically adjust column widths.

```latex
\usepackage{tabularx}
...
\begin{tabularx}{\textwidth}{|X|X|X|}
\hline
Column 1 & Column 2 & Column 3 \\ 
\hline
Data 1   & Data 2   & Data 3   \\ 
\hline
\end{tabularx}
```

- `X`: Flexible-width columns that expand to fill the line.

#### **Long Tables**

For tables spanning multiple pages, use the `longtable` package.

```latex
\usepackage{longtable}
...
\begin{longtable}{|c|c|c|}
\hline
Header 1 & Header 2 & Header 3 \\ 
\hline
\endfirsthead
\hline
Header 1 (Cont.) & Header 2 (Cont.) & Header 3 (Cont.) \\ 
\hline
\endhead
Data 1 & Data 2 & Data 3 \\
\hline
\end{longtable}
```

---

### **Combining Tables with Color**

Use the `colortbl` package to add color.

```latex
\usepackage{colortbl}
\usepackage[table,xcdraw]{xcolor}
...
\begin{tabular}{|c|c|}
\hline
\rowcolor{gray!30} Header 1 & Header 2 \\ 
\hline
Data 1   & Data 2   \\ 
\hline
\end{tabular}
```

---

### **Example of a Full Table**

```latex
\documentclass{article}
\usepackage{tabularx}
\usepackage{booktabs}
\usepackage{xcolor}

\begin{document}

\begin{table}[h!]
\centering
\begin{tabularx}{\textwidth}{|X|X|X|}
\hline
\rowcolor{gray!30} Column 1 & Column 2 & Column 3 \\ 
\hline
Data 1   & Data 2   & Data 3   \\ 
Data 4   & Data 5   & Data 6   \\ 
\hline
\end{tabularx}
\caption{A sample wide table with colors.}
\end{table}

\end{document}
```

---
## New Page
To jump to a new page in LaTeX, you can use the `\newpage` or `\clearpage` commands. Here's how each command works:

---

### **1. Using `\newpage`**

The `\newpage` command forces the content following it to start on a new page. It doesn't process pending figures or tables that are floating.

#### Example:

```latex
\documentclass{article}
\begin{document}

This is the first page.

\newpage % Forces a new page

This is the second page.

\end{document}
```

---

### **2. Using `\clearpage`**

The `\clearpage` command not only starts a new page but also ensures that all pending floating elements (e.g., figures, tables) are processed before the page break.

#### Example:

```latex
\documentclass{article}
\begin{document}

This is the first page.

\clearpage % Forces a new page and processes floating elements

This is the second page.

\end{document}
```

---

### **3. Page Breaks in Specific Environments**

#### **Manual Page Break in Long Documents**

For long documents, you can manually insert page breaks:

```latex
\section{Introduction}
Content for the first section.

\newpage

\section{Next Section}
Content for the next section.
```

---

### **4. Starting a New Page for Chapters (Book/Report Class)**

In `book` or `report` classes, chapters automatically begin on a new page. If you want to manually force a new chapter to start, you can use:

```latex
\chapter{New Chapter}
```

---

### **5. Adding Blank Pages**

To insert a completely blank page:

- Use the `\null` command with `\newpage`:

```latex
\null
\newpage
```

- Or use the `emptypage` package to insert a blank page:

```latex
\usepackage{emptypage}
\newpage
```

---

### **6. Using `\pagebreak`**

The `\pagebreak` command allows you to suggest a page break, giving LaTeX flexibility to decide whether to break the page.

#### Example:

```latex
This is a long paragraph.

\pagebreak % Suggests a page break here

Another paragraph starts here.
```

---

### **7. Preventing Page Breaks**

To avoid breaking a page at a specific point, use `\nopagebreak`:

```latex
This is the first part of a paragraph.

\nopagebreak % Prevents a page break here

Continuation of the paragraph.
```

---

### Summary of Commands:

|Command|Description|
|---|---|
|`\newpage`|Forces content to start on a new page without processing pending floats.|
|`\clearpage`|Forces content to start on a new page and processes all pending floats.|
|`\pagebreak`|Suggests a page break at the specified location.|
|`\nopagebreak`|Prevents a page break at the specified location.|

By combining these commands, you can control page breaks effectively in LaTeX!

## Table of figures
In LaTeX, **figures** do not appear in the **Table of Contents (TOC)** by default. However, you can generate a **Table of Figures** separately and also include the figures in the global table of contents if needed.
### **1. Table of Figures**
To generate a Table of Figures, you can use the `\listoffigures` command. This will create a list of all figures with their captions, similar to how the Table of Contents lists the sections.
#### Example:

```latex
\documentclass{article}
\usepackage{graphicx}

\begin{document}

\tableofcontents % This generates the Table of Contents
\listoffigures % This generates the Table of Figures

\section{Introduction}
Here is the introduction text.

\begin{figure}[h]
    \centering
    \includegraphics[width=0.5\textwidth]{example-image}
    \caption{This is an example figure.}
    \label{fig:example}
\end{figure}

\end{document}
```

- The `\listoffigures` command should be placed where you want the Table of Figures to appear, typically after `\tableofcontents`.
### **2. Including Figures in the Global Table of Contents**
If you want **figures** to show up directly in the **global Table of Contents**, you need to treat them like sections (which is unconventional, but possible). To achieve this, you can use the `\addcontentsline` command to manually add an entry for the figure in the TOC.
#### Example:

```latex
\documentclass{article}
\usepackage{graphicx}

\begin{document}

\tableofcontents % Table of Contents

\section{Introduction}
This is the introduction.

% Manually add figure to Table of Contents
\begin{figure}[h]
    \centering
    \includegraphics[width=0.5\textwidth]{example-image}
    \caption{This is a figure added to the TOC.}
    \label{fig:example}
    \addcontentsline{toc}{section}{Figure 1: This is a figure added to the TOC}
\end{figure}

\end{document}
```
In this example:
- The `\addcontentsline{toc}{section}{Figure 1: ...}` adds an entry for the figure to the Table of Contents under the section category. You can adjust the level (`section`, `subsection`, etc.) as needed.
---