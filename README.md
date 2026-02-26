# My personal homepage

## About

Static website and blog, build with [Quarto][1] and hosted on GitHub pages.

## Prerequisites

- [Quarto][1]
- [Task][2]

## Usage

### Editing and publishing website content

1. Make changes to the relevant qmd file
1. Commit and push changes to main branch

The [deploy workflow](.github/workflows/deploy.yml) will take care of rendering and updating the website.

### Creating blog posts

1. Create a new draft post via `task new-post POST_NAME=<HYPHEN-DELIMITED-NAME-OF-POST>`
1. Add content to newly created `index.qmd` file
1. Commit changes and push to main


[1]: https://quarto.org/
[2]: https://taskfile.dev/
