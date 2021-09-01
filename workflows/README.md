This folder contains a selection of public composite actions.

See [this](https://github.com/actions/runner/issues/646#issuecomment-901336347) post detailing how to run a remote composite action. 
Briefly explained, an action contained here (or in any public repo) can be run from another repo, like this:

```yaml
name: coverage

on:
  pull_request:
  push:
    branches:
      - master

jobs:
  codecov:
    runs-on: ubuntu-latest
    steps:
      - uses: snok/.github/workflows/codecov@main
        with:
          source-dir: src
          pip-cache-key: 0
          poetry-cache-key: 0
          python-version: 3.9

```

So instead of having an identical copy of generic workflows like our `codecov` workflow in every repo,
we can just keep it here, and reference it in each of the child repos.
