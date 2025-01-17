# goreleaser-action

The `goreleaser` GitHub action with automatic tagging.

## Usage

In your GitHub workflow, add a job as follows.

```yaml
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - id: version
        run: echo version=$SOME_VERSION > ${{ github.output }}
      - uses: raviqqe/goreleaser-action@v1
        with:
          version: ${{ steps.version.outputs.version }}
          snapshot: ${{ github.ref != 'refs/heads/main' }}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## License

[The Unlicense](UNLICENSE)
