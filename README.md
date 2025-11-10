# Github Reusable Workflows

Collection of reusable Github Workflows & Actions.

## Usage
Some basic usage examples for both workflows & actions.

**Actions**
```yaml
name: Release
on:
  push: main

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Semantic Release
        id: release
        uses: Byrde/github-reusable-workflows/actions/semantic-release@main
        with:
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Resolved Version
        run: echo "Version is ${{ steps.release.outputs.version }}"
```

**Workflows**
```yaml
name: Example
on:
  pull_request:
    types: [closed]

jobs:
  apply:
    uses: Byrde/github-reusable-workflows/.github/workflows/example.yml@main
    with:
      environment: production
```