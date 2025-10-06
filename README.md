# Cookiecutter Research Project

A template for a modern, fully featured and efficient research project.

![cookiecutter research project logo](cookiecutter_logo.svg)

## Setup

Prerequisites:

- the Python [package manager uv](https://docs.astral.sh/uv/)
- `cookiecutter` package (link [here](https://github.com/cookiecutter/cookiecutter))
- an installation of [Quarto](https://quarto.org/)
- an installation of [LaTeX](https://www.latex-project.org/)

## Features

- a well-designed folder structure with folders for data at different stages, models, notebooks, code, and outputs.
- sensible defaults on which of these folders are ignored by git (via a .gitignore file). For example, code, references, paper, and slides folders are under version control. But data, logs, outputs, and so, folders are not.
- a .env file for storing secrets—researchers are increasingly using cloud computer to do research (see this post for doing this with VS Code and Google Cloud.)
- pre-commit with Ruff (linting, formating, import sorting), nbstripout, end of file fixer, large file check, trailing whitespace fixer, and toml/yaml checks.
- uv for managing the Python environment, and making it reproducible via the lockfile.
- a Makefile with commands for installing the environment (for reproducibility), and for compiling the paper, and the slides.
- paper and slides based on Quarto. These can be set to automatically update as your code outputs update.
- a project config TOML file where global project settings can be stored. For example, you could have all your chart configurations here, or the hyperparameter settings.
- support for references in a .bib file and citations defined in a .csl (csl = citation style language) file. You can find a very long list of citation styles, including for most major journals, [here](https://github.com/citation-style-language/styles).
- support for code execution in the paper and slides, including in-line via `python f"{number}"` syntax

Read more in the [accompanying blog post](https://aeturrell.com/blog/posts/ultra-modern-python-cookiecutters/#cookiecutter-research-project).

## How to use this template

To install cookiecutter, which will help you populate the template with details like your project's name, run

```bash
uv tool install cookiecutter
```

To create a new project folder based on this cookie cutter:

```bash
uv tool run cookiecutter https://github.com/aeturrell/cookie-cutter-research-project.git
```

The new project folder will appear within the folder you ran the command in.

## Working on your project

This assumes you are in the project root.

First, run `uv sync` to create the Python environment (it installs into `.venv`)

To create the paper, use `make paper`.

To create the slides, use `make slides`.

## You might also like

Looking for further reproducible research inspiration? Check out this [worked example](https://github.com/aeturrell/example-reproducible-research) of a reproducible research project.

## Top tips

For Quarto documents (paper and slides), the root is the project root. To properly reference markdown images in another folder using project root, begin with a forward slash, eg:

```markdown
![](/outputs/missingness.svg)
```

or, for latex

```markdown
{{< include /outputs/equation.tex >}}
```
