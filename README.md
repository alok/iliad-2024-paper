# Build Instructions for *Lean 4 for Software Engineering*

This document provides instructions for building the NeurIPS 2024 paper titled "**Lean 4 for Software Engineering**" by Alok Singh.

## Prerequisites

Ensure that you have the following installed:

- **LaTeX Distribution**: We recommend [TeX Live](https://www.tug.org/texlive/) or [MiKTeX](https://miktex.org/).
- **XeLaTeX**: The paper uses XeLaTeX for compilation.
- **Python**: Required for the `minted` package used for syntax highlighting.
- **Pygments**: A Python library for lexical analysis and syntax highlighting.

  Install Pygments using:
  ```bash
  pip install Pygments  ```

## Building the Paper

To compile the paper, follow these steps:

1. **Clone the Repository**

   If the project is hosted on a version control system like Git, clone the repository:
   ```bash
   git clone <repository_url>   ```

   Replace `<repository_url>` with the actual URL of the repository.

2. **Navigate to the Project Directory**
   ```bash
   cd <project_directory>   ```

   Replace `<project_directory>` with the path to the cloned repository.

3. **Compile the Document**

   Use the following commands to compile the paper:
   ```bash
   xelatex -shell-escape neurips_2024.tex
   bibtex neurips_2024
   xelatex -shell-escape neurips_2024.tex
   xelatex -shell-escape neurips_2024.tex   ```

   - The `-shell-escape` flag is required for the `minted` package to function properly.
   - Running `xelatex` multiple times ensures that all references and citations are updated correctly.
   - The `bibtex` command processes the bibliography from `neurips_2024.bib`.

4. **Alternative: Using `latexmk`**

   For automated compilation, you can use `latexmk`:
   ```bash
   latexmk -xelatex -shell-escape neurips_2024.tex   ```

   This command handles multiple runs and bibliography processing automatically.

## Notes

- **Bibliography**: The paper includes citations managed in `neurips_2024.bib`. Ensure that you run `bibtex` or use `latexmk` to process the bibliography correctly.

- **VSCode Configuration**: A `.vscode/settings.json` file is included for those who use Visual Studio Code. It provides recommended settings for working with LaTeX projects, such as:
  ```json:.vscode/settings.json
  {
    "latex-workshop.latex.tools": [
      {
        "name": "xelatex",
        "command": "xelatex",
        "args": [
          "-shell-escape",
          "-synctex=1",
          "-interaction=nonstopmode",
          "%DOC%"
        ]
      }
    ],
    "latex-workshop.latex.recipes": [
      {
        "name": "xelatex",
        "tools": ["xelatex"]
      }
    ],
    "latex-workshop.view.pdf.viewer": "tab"
  }  ```

  - These settings configure LaTeX Workshop to use XeLaTeX with the necessary flags.
  - The PDF viewer is set to open in a new tab within VSCode.

- **Missing Packages**: If you encounter errors about missing LaTeX packages, install them using your LaTeX distribution's package manager. For TeX Live, use:
  ```bash
  tlmgr install <package-name>  ```

  Replace `<package-name>` with the name of the missing package.

- **Font Issues**: Since XeLaTeX supports UTF-8 and uses system fonts, ensure that the required fonts are installed on your system. If the document uses specific fonts, they should be included or specified.

- **Python Version**: Make sure you have Python 3.x installed. You can check your Python version with:
  ```bash
  python --version  ```

## Helpful Tips

- **Cleaning Auxiliary Files**: To clean up auxiliary files generated during compilation, run:
  ```bash
  latexmk -c  ```

- **Continuous Preview**: If you're editing the document and want continuous compilation and preview, use:
  ```bash
  latexmk -pvc -xelatex -shell-escape neurips_2024.tex  ```

  - The `-pvc` flag tells `latexmk` to preview and continuously update the PDF as you save changes.

- **Error Troubleshooting**:

  - **Common Errors**: If you encounter errors related to the `minted` package, ensure that:

    - The `-shell-escape` flag is used.
    - Pygments is installed and accessible to your LaTeX distribution.

  - **Overfull/Underfull Boxes**: These warnings can often be ignored, but if they affect the layout, adjust the content accordingly.

- **Graphics and Images**:

  - Place any images in a directory (e.g., `images/`) and include them using:
    ```latex
    \includegraphics[width=\linewidth]{images/your_image.png}    ```

  - Ensure that image files are in a format supported by LaTeX (e.g., PNG, PDF, EPS).

## Project Structure

- **`neurips_2024.tex`**: The main LaTeX source file.
- **`neurips_2024.bib`**: Bibliography file containing references.
- **`.vscode/`**: Contains workspace settings for Visual Studio Code.
- **`.cursorrules`**: Configuration files for cursor-based rules (if applicable).
- **`README.md`**: This instruction manual.

## Collaboration Guidelines

- **Git Branching**: If using Git, create a new branch for your changes:
  ```bash
  git checkout -b your-feature-branch  ```

- **Pull Requests**: Submit your changes via pull requests for review.

- **Commit Messages**: Use clear and descriptive commit messages.

- **Communication**: For discussions and clarifications, feel free to reach out via email or the project's communication channel.

## Contact

If you have any questions or encounter issues, please contact:

- **Alok Singh**
  - Email: [alokbeniwal@gmail.com](mailto:alokbeniwal@gmail.com)
