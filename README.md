# PRLint Reloaded

A GitHub Action that validates PR titles.

## Usage

Add a `.github/workflows/prlint.yml` file to your repository with the following content:

```yml
name: PR Lint
on:
  pull_request:
    types: ['opened', 'edited', 'reopened', 'synchronize']
jobs:
  prlint-reloaded:
    runs-on: ubuntu-latest
    steps:
      - uses: maor-rozenfeld/prlint-reloaded@actions
        with:
          title-regex: "^[A-Z][a-z]+?\\s"
          error-message: Your title must start with a capital letter, and a real word, e.g. 'Add GO support'
      - uses: maor-rozenfeld/prlint-reloaded@actions
        with:
          title-regex: "^\\S+\\s+\\S+\\s+\\S+"
          error-message: Your title must have at least three words
      - uses: maor-rozenfeld/prlint-reloaded@actions
        with:
          title-regex: "^(?!\\S+ing\\s)(?!\\S+ed\\s)"
          error-message: Use imperative mood (i.e write "Fix", not "Fixed" or "Fixing")
```

## License

[MIT](/LICENSE)
