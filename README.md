# renderCommutativeDiagram

A little Bash script for rendering snippets of TeX code as commutative diagrams (cropped and converted into SVG format).

### Usage

Given a text file `example.tex` with a definition of a commutative diagram in the format of Paul Taylor's *Commutative Diagrams* TeX package, we can invoke this script as follows:

    renderCommutativeDiagram example.tex

and it will generate an image `example.svg`.

### Installation

There is no installation script, dependencies must be installed manually, then the script itself must be modified (one single path must be set to point to a specific file, as described below).

The script depends on the following tools:

  * `pdflatex`
  * `pdfcrop`
  * `pdf2svg`

These tools must be installed on your system. If those tools are not available, the script will print an error message and a hint how to install those tools using `apt` package manager.

The script also requires the source of [Paul Taylor's diagrams package](https://www.paultaylor.eu/diagrams/). Once the file is downloaded, a path inside of the script must be adjusted accordingly (open the script with a text editor, search for "ADJUST").

If you want to use more packages, you can modify the prepended header inside the script (search for `usepackage` there).

### Example

Assume that we are given the following diagram definition (`example.tex`, contained in this repository):

    GFGFC & \pile{
      \rTo^{GFh} \\ 
      \rTo_{G\epsilon_{FC}}
    }             &  GFC   &  \rTo^{h}                         & C \\
    \dEq  &       &  \dEq  &                                   & \dDashto_{\lambda} \\
    GFGFC & \pile{
      \rTo^{GFh} \\ 
      \rTo_{G\epsilon_{FC}} 
    }             & GFC    & \rTo_{\hspace{1em}Ge\hspace{1em}} & GL(C, h) \\
          &       &        &                                   &     \\
    FGFGA & \pile{
      \rTo^{\hspace{0.8em}FG\epsilon_A\hspace{0.8em}} \\ 
      \rTo_{\epsilon_{FGA}}
    }             & FGA    & \rOnto                            & LKA \\
          &       &        & \rdTo_{\epsilon_A}                & \dDashto_{\kappa_A} \\
          &       &        &                                   & A

Invoking

    renderCommutativeDiagram example.tex

will create a file `example.svg` that looks as follows:

![commutative diagram](./example.svg)

*(The two diagrams are a quote from Mac Lane, Moerdijk "Sheaves in Geometry and Logic", Springer, 1991, pp. 179-180)*

