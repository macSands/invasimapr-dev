# Contributing to invasimapr

First off, thanks for considering contributing to invasimapr!

## How to contribute

### Report bugs

Report bugs at https://github.com/macSands/invasimapr-dev/issues.

If you are reporting a bug, please include:

- Your operating system name and version.
- Any details about your local setup that might be helpful in troubleshooting.
- Detailed steps to reproduce the bug.

### Fix bugs

Look through the GitHub issues for bugs. Anything tagged with "bug" and "help
wanted" is open to whoever wants to implement it.

### Propose features

The best way to send feedback is to file an issue at
https://github.com/macSands/invasimapr-dev/issues.

If you are proposing a feature:

- Explain in detail how it would work.
- Keep the scope as narrow as possible, to make it easier to implement.

### Submit changes

Ready to contribute? Here is how to set up `invasimapr` for local development.

1. Fork the `invasimapr-dev` repo on GitHub.
2. Clone your fork locally.
3. Create a branch for local development:

    ```
    git checkout -b name-of-your-bugfix-or-feature
    ```

4. Make your changes. Make sure to:
    - Follow the [tidyverse style guide](https://style.tidyverse.org/).
    - Add or update roxygen2 documentation for any changed functions.
    - Add or update tests as needed.
    - Run `devtools::check()` to ensure there are no errors.

5. Commit your changes and push your branch to GitHub:

    ```
    git commit -m "Brief description of changes"
    git push origin name-of-your-bugfix-or-feature
    ```

6. Submit a pull request through GitHub.

### Pull request guidelines

Before a pull request is merged, it should:

- Include tests for any new functionality.
- Pass `devtools::check()` without errors.
- Update documentation if needed (`devtools::document()`).

## Acknowledgments

This contributing guide is adapted from the [usethis contributing template](https://usethis.r-lib.org/reference/use_tidy_contributing.html).
